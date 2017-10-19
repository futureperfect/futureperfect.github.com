---
layout: post
title: Functional State Encapsulation
tags: [til]
---

Today I came across an interesting example in Scheme of functional state
encapsulation and the utility of procedures as first-class language constructs.
It's interesting to consider procedures as vehicles for state encapsulation in
the same way that objects are described to be.

The following is an example of a procedure `make-monitored`, which takes in a
procedure and produces a version of the procedure that maintains a count of how
many times it has been invoked since being monitored. Passing a special symbol
as an argument causes the internal dispatch method to return the count or reset
the counter.

```racket
(define (make-monitored procedure)
  (define counter 0)
  (define (dispatch . m)
    (cond [(eq? (car m) 'how-many-calls?) counter]
          [(eq? (car m) 'reset-counter) (begin
                                          (set! counter 0)
                                          counter)]
          [else (begin
                  (set! counter (+ 1 counter))
                  (apply procedure m))]))
  dispatch)


> (define monitored-sqrt (make-monitored sqrt))
> (monitored-sqrt 14)
3.7416573867739413
> (monitored-sqrt 'how-many-calls?)
1
> (monitored-sqrt 'reset-counter)
0
```
