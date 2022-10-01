# Exercise Z3

- [ ] Follow the [Z3 Playground](https://jfmc.github.io/z3-play/) up to Bitvectors (don't read Bitvectors).

> :warning: Some browsers might not run the playground properly. Safari is a browser we know doesn't work well. Chrome, Chromium, Firefox, and Brave browsers have been tested to work fine.

- [ ] Use Z3 to find a solution for the following puzzle:
</br>
<img src="images/Logic_Puzzle1.png" width="350">

    Solution : 
<pre>
    <code>
        (declare-const a Int)
        (declare-const b Int)
        (declare-const c Int)
        (assert  (= (+ a a ) 10))
        (assert (= (+ (* a b) b) 12))
        (assert (= (- (* a b) (* c a)) a))
        (check-sat)
        (get-model)
    </code>    
</pre>

    Result : 
<pre>
    <code>
        sat //satisfable => there is a solution
        (
        (define-fun a () Int
            5)
        (define-fun c () Int
            1)
        (define-fun b () Int
            2)
        )
    </code>    
</pre>

- [ ] Write a formula to check if the following two equations are equivalent:
</br>
<img src="images/Logic_Puzzle2.png" width="350">

Solution : 
<pre>
    <code>
        (declare-const p Bool)
        (declare-const q Bool)
        (define-fun equivalent () Bool  
            (= (and (=> (and p q) p) (=>  p (and p q))) (=> p q)))
        (assert (not equivalent))
        (check-sat)
    </code>    
</pre>

    Result : 
<pre>
    <code>
        unsat //  **F** is *valid* precisely when **not F** is not satisfiable (unsatisfiable)
    </code>    
</pre>

- [ ] A good additional practice will be to try and prove questions in [this file](AdditionalExerciseForSMT.pdf)

> :information_source: You might find the [cheat sheet](Cheat_Sheet.md) useful for the exercises and additional explanations of the Z3 principles.
