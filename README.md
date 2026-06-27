# Beta Change Pack 27.6.26

## What this update fixes/adds

1. Personal student links show on the student home page only.
2. Subject Links schema-cache error is fixed with exact RPC functions.
3. Teacher Activity now has filters:
   - Grade
   - Student
   - Subject
   - Quiz
   - Activity type
   - Date range
4. Teacher can load score summaries:
   - latest score
   - best score
   - average score
   - number of attempts
   - total score
5. Students tab has search/filter.
6. Message box added:
   - student sends message from home page
   - teacher replies from Teacher Admin
   - unread badge for teacher
7. Images tab improved:
   - choose grade
   - choose subject
   - choose quiz
   - choose question
   - upload/select image
   - attach image to question
8. Every quiz attempt is saved as a new result row.

## Setup

1. Run `supabase_beta_change_pack_27_6_26.sql` in Supabase SQL Editor.
2. Upload `index.html` to GitHub.
3. Rename it exactly to `index.html`.
4. Refresh your website.

## Important

If Supabase still shows schema-cache error after running SQL:
- Wait 30 seconds
- Refresh the website
- Run this again in SQL Editor:

```sql
notify pgrst, 'reload schema';
```
