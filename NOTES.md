# Patch Exercise Notes

## Bugs Fixed

1. **Search/status filter SQL precedence**
   - Fixed the task search query by grouping the title/description search conditions before applying the optional status filter.
   - This prevents incorrect results caused by SQL AND/OR operator precedence.

2. **Artificial API response delay**
   - Removed the artificial `Thread.sleep()` delay from `TaskController`.
   - The delay was based on query length and unnecessarily slowed API responses.

3. **Frontend loading state after API failure**
   - Updated `useTasks.js` to clear previous errors when a new request starts and to always reset `loading` using `finally()`.
   - This prevents the UI from remaining in a loading state after an API failure.

## What I Did Not Change

I did not rewrite the application architecture or modify unrelated features. Pagination, UI design, database structure, and other existing functionality were left unchanged because they were outside the highest-value fixes identified during the timebox.

## Biggest Remaining Risk

Additional edge cases may remain outside the tested search/filter and API failure flows, particularly around pagination and broader input handling.

## Tools / AI Used

I used the project documentation, local browser/API testing, Git diff/status, and AI assistance to inspect the code, reason about bugs, and review focused fixes. I verified the changes by running and testing the backend and frontend.