\# Patch Notes



\## Summary

Fixed four issues across SQL, backend, and frontend:

\- Corrected search/status SQL precedence by grouping title and description conditions.

\- Removed an artificial Thread.sleep delay from the search API.

\- Improved frontend request handling by ignoring stale responses and resetting error/loading state.

\- Added validation so invalid status and pagination inputs return HTTP 400.



\## What I Did Not Change

I did not add debounce, wildcard escaping, or move pagination into the database because these were lower priority for the timebox. I also left the existing in-memory pagination design unchanged.



\## Biggest Remaining Risk

Pagination is currently performed in memory after fetching tasks. This would not scale well for a larger dataset; database-level pagination would be preferable.



\## Tools / AI Used

I used Claude to inspect the code and help draft possible fixes. I reviewed the suggested changes, applied the relevant changes, and verified the application locally using the available API checks and frontend build.



\## Local Verification

\- Backend started successfully on port 8080.

\- `q=api` returned 8 results with no archived tasks.

\- `q=api\&status=OPEN` returned 6 OPEN results.

\- Invalid status returned HTTP 400.

\- `page=0` returned HTTP 400.

\- `npm run build` completed successfully.

