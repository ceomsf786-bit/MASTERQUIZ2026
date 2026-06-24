# School Quiz Hub

This is a GitHub Pages + Supabase quiz system.

## What it does

- One website for **Grade 4 to Grade 11**
- Learners can only enter grades you approve in Supabase
- Learner login uses approved name + learner code
- Learners can upload an avatar image
- Subjects and quizzes come from Supabase
- Supported question types: `mcq`, `mcq_image`, `true_false`, `missing_word`, `multi_select`, `match`, `short_exact`
- The browser does **not** receive the correct answers
- Supabase marks the quiz through a function
- Results save live
- Leaderboard supports grade, subject and quiz view

## Files

| File | Use |
|---|---|
| `index.html` | Upload this to GitHub Pages |
| `supabase_schema.sql` | Paste into Supabase SQL Editor and run |
| `student_upload_template.csv` | Import learners into `student_uploads` |
| `question_upload_template.csv` | Import questions into `question_uploads` |

## Setup steps

### 1. Create Supabase project

Create a new Supabase project, for example:

```text
school-quiz-system
```

### 2. Run SQL

In Supabase:

```text
SQL Editor → New query → paste supabase_schema.sql → Run
```

### 3. Get Supabase URL and key

Copy your:

```text
Project URL
Publishable key / anon public key
```

### 4. Put them into `index.html`

Find:

```js
const SUPABASE_URL = "PASTE_SUPABASE_URL_HERE";
const SUPABASE_PUBLISHABLE_KEY = "PASTE_SUPABASE_PUBLISHABLE_KEY_HERE";
```

Replace with your own Supabase details.

Never put your **service role key** into GitHub.

### 5. Upload to GitHub

Upload `index.html` to a new GitHub repository, then enable GitHub Pages.

## Demo login after SQL setup

```text
Grade: 6
Student: Demo Grade 6 Learner
Code: G6-001
```

or

```text
Grade: 6 or 7
Student: Demo Multi Grade Learner
Code: MULTI-001
```

## Adding learners

Import `student_upload_template.csv` into:

```text
student_uploads
```

Then run:

```sql
select public.process_student_uploads();
```

## Adding questions

Import `question_upload_template.csv` into:

```text
question_uploads
```

Then run:

```sql
select public.process_question_uploads();
```

This creates/updates subjects, quizzes and questions. You do not need to copy IDs.

## Question format examples

### MCQ

```json
options:
[
  {"value":"A","label":"10"},
  {"value":"B","label":"12"}
]

correct_answer:
"B"
```

### True / False

```json
correct_answer:
"true"
```

### Missing word

```json
correct_answer:
"numerator"

accepted_answers:
["top number"]
```

### Multi-select

```json
options:
[
  {"value":"A","label":"2 is even"},
  {"value":"B","label":"3 is odd"},
  {"value":"C","label":"5 is even"}
]

correct_answer:
["A","B"]
```

### Match

```json
options:
{
  "left":["Numerator","Denominator"],
  "right":["Bottom number","Top number"]
}

correct_answer:
{
  "Numerator":"Top number",
  "Denominator":"Bottom number"
}
```

## Image questions

Put the image URL into:

```text
image_url
```

For `mcq_image`, use the same MCQ options format.

## Recommended workflow

```text
1. Add approved learners to student_uploads
2. Run process_student_uploads()
3. Add questions to question_uploads
4. Run process_question_uploads()
5. Learners open the GitHub Pages quiz website
6. Learners login
7. Learners complete quizzes
8. Results show live on leaderboard
```
