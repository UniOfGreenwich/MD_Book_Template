# Quiz



~~~admonish important 

As of Version 1.1.0 this MDBook template now has the capability to embedded quizzes into markdown book, using:

- https://github.com/cognitive-engineering-lab/mdbook-quiz/releases/tag/v0.3.10

~~~


First, create a quiz file. Quizzes are encoded as TOML files (see [Quiz schema](https://github.com/cognitive-engineering-lab/mdbook-quiz#quiz-schema)). For example

```toml
# quizzes/rust-variables.toml
[[questions]]
type = "ShortAnswer"
prompt.prompt = "What is the keyword for declaring a variable in Rust?"
answer.answer = "let"
context = "For example, you can write: `let x = 1`"
```

~~~admonish important

When running mdbook-quiz locally, or when you check the source code for the deployment each question will have an`id` field auto generated 

~~~


and in the markdown file: 

```md
And now, a _quiz_:

{{#<type> ./quizzes/rust-variables.toml}}}

```

~~~admonish warning

Replace `<type>` with `quiz`

~~~

And now, a _quiz_:

{{#quiz ./quizzes/quiz_1.toml}}


Here is a multiple choice example: 

```toml
[[questions]]
type = "MultipleChoice"
prompt.prompt = "What does it mean if a variable `x` is immutable?"
prompt.distractors = [
  "`x` is stored in the immutable region of memory.",
  "After being defined, `x` can be changed at most once.",
  "You cannot create a reference to `x`."
]
answer.answer = "`x` cannot be changed after being assigned to a value."
context = """
Immutable means "not mutable", or not changeable.
"""
```

{{#quiz ./quizzes/quiz_2.toml}}

You can have more than one question per quiz, by stacking quizzes into one file `<nameofquiz>.toml`, the beauty is if you don't get them all correct you can revist the ones you got wrong. 

~~~admonish warning

Remember that question `id` is unique, so if you copy and paste repeated questions, remember to remove the `id` field

~~~

{{#quiz ./quizzes/quiz_3.toml}}