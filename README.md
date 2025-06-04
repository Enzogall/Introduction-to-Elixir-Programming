# Introduction to Elixir Programming

Welcome! In this workshop you’ll deepen your understanding of Elixir’s core concepts, pattern matching, recursion, the `Enum` and `String` modules, pipelines, and basic CLI scripting, by tackling a series of increasingly challenging exercises. We’ll be using [Elixir Playground](https://playground.functional-rewire.com/) so no local install is required.

Official docs:  
- Elixir guide: https://elixir-lang.org/getting-started/introduction.html  
- `Kernel` and pattern matching: https://hexdocs.pm/elixir/Kernel.html  
- `Enum` module: https://hexdocs.pm/elixir/Enum.html  
- `String` module: https://hexdocs.pm/elixir/String.html  
- Mix and escript: https://hexdocs.pm/mix/Mix.Tasks.Escript.Build.html  

---

## Exercise 1: Even numbers 1–50  
**Goals:** recursion and guards, list comprehensions, `Enum.filter` and pipelines  

1. Write `print_evens/1` that  
   - recursively traverses `1..n` with a guard to print only even numbers.  
   - call it as `print_evens(50)`.  

2. Rewrite using a list comprehension:  
   ```elixir
   for i <- 1..50, rem(i, 2) == 0, do: IO.puts(i)
   ```  

3. Finally, compose with `Enum.filter/2` and the pipeline operator (`|>`).  

References:  
- Recursion and guards: https://elixir-lang.org/getting-started/recursion.html
- Comprehensions: https://hexdocs.pm/elixir/Kernel.SpecialForms.html#for/1  
- Enum.filter: https://hexdocs.pm/elixir/Enum.html#filter/2  

---

## Exercise 2: Multiply two numbers  
**Goals:** basic function clauses, tail recursion and higher-order functions  

1. Define `multiply(a, b)` that returns `a * b`.  
2. Implement `multiply_list(list)` that returns the product of all elements in a list using  
   - a simple recursion  
   - a tail-recursive version with an accumulator  
   - `Enum.reduce/3`  

References:  
- Recursion and tail recursion: https://elixir-lang.org/getting-started/recursion.html  
- `Enum.reduce`: https://hexdocs.pm/elixir/Enum.html#reduce/3  

---

## Exercise 3: Convert string to uppercase  
**Goals:** `String` module, charlists vs binaries and pattern matching  

1. Using `String.upcase/1`, write `to_upper/1`.  
2. Accept both Elixir binaries and charlists, convert charlists (`'hello'`) to binaries first, then upcase.  

References:  
- Binaries and charlists: https://hexdocs.pm/elixir/binaries-strings-and-charlists.html
- String module: https://hexdocs.pm/elixir/String.html   

---

## Exercise 4: Count characters in a sentence  
**Goals:** pipelines, regex or comprehensions and `String` functions  

Write `count_chars/1` that takes a sentence, strips out all whitespace, and returns the character count. Solve at least two ways:  

- Using `String.replace/3` and `String.length/1`.  
- Splitting into graphemes with `String.graphemes/1` then `Enum.count/1`.  

References:  
- `String.replace`: https://hexdocs.pm/elixir/String.html#replace/3  
- `String.graphemes`: https://hexdocs.pm/elixir/String.html#graphemes/1  

---

## Exercise 5: Find the maximum in a list  
**Goals:** recursion, `Enum.max/1` and error handling  

1. Implement `my_max/1` that finds the max via recursion and pattern matching on `[head | tail]`.  
2. Compare to `Enum.max/1`.  
3. Add error handling: when given an empty list, return `{:error, :empty_list}`.  

References:  
- `Enum.max`: https://hexdocs.pm/elixir/Enum.html#max/1  

---

## Exercise 6: Factorial of a number  
**Goals:** recursive definitions, math and tail recursion  

1. Write `fact/1` recursively with a guard for `n < 0` to return `{:error, :negative}`.  
2. Implement a tail-recursive version.  

References:  
- Writing tail recursion: https://hexdocs.pm/elixir/recursion.html 

---

## Exercise 7: Primality and prime sieve  
**Goals:** guards, recursion, `Enum.filter` and Streams  

1. `is_prime?/1`: check divisibility up to `sqrt(n)`.  
2. `primes_up_to/1`: generate all primes `n` by filtering `2..n`.  
3. Implement the Sieve of Eratosthenes using recursion and Streams.  

References:  
- Streams: https://hexdocs.pm/elixir/Stream.html  

---

## Exercise 8: Word frequency counter  
**Goals:** string processing, maps, `Enum.frequencies/1` and sorting  

Write `word_freq/1` that:  
1. Takes a paragraph `String.t()`.  
2. Downcases, removes punctuation (use `Regex.replace/4`).  
3. Splits on whitespace.  
4. Returns a map of word to count, sorted by descending frequency.  

References:  
- `Enum.frequencies`: https://hexdocs.pm/elixir/Enum.html#frequencies/1  
- Regex: https://hexdocs.pm/elixir/Regex.html  

---

## Final Task: Build a CLI calculator escript  
**Goals:** Mix project, escript, `System.argv/0`, pattern matching and error handling  

1. `mix new calc --module Calculator --app calc`  
2. In `lib/calculator.ex`, implement:
   - `main/1` to receive `args :: [String.t()]`.  
   - Pattern-match `["add", a, b]`, `["subtract", a, b]`, `["multiply", a, b]`, `["divide", a, b]`.  
   - Convert `a`, `b` to integers, handle parse errors and division by zero.  
   - `IO.puts/1` with the result or error.  
3. In `mix.exs`, add:
   ```elixir
   escript: [main_module: Calculator]
   ```
4. Run:
   ```
   mix escript.build
   ./calc add 10 5 # ⇒ 15
   ./calc divide 4 0 # ⇒ error message
   ```

5. Write a few ExUnit tests in `test/calculator_test.exs`.  
- ExUnit docs: https://hexdocs.pm/ex_unit/ExUnit.html  

---

By the end of these exercises you’ll have practiced pure functions, recursion, the powerful `Enum` and `String` modules, pipeline composition, basic error handling, and even shipped a small CLI tool. Happy coding!
