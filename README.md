# Firebase Transaction Silent Failure
This repository demonstrates an uncommon bug in Firebase transactions where multiple updates within a single transaction can silently fail, resulting in inconsistent data. The primary issue lies in the lack of comprehensive error handling within the transaction callback function. If any of the update operations encounter an error, the entire transaction should be rolled back to maintain data integrity. This example showcases the problematic code and provides a corrected version with proper error handling.

## Steps to Reproduce
1.  Clone this repository.
2.  Install Firebase (npm install firebase).
3.  Configure Firebase with your project details (replace placeholders in `bug.js`).
4.  Run `node bug.js`. Observe the inconsistent data after execution.
5.  Run `node bugSolution.js`. Verify the corrected behavior and data consistency.

## Solution
The solution involves adding robust error handling to the transaction callback.  Any error during the transaction should trigger a `reject` to roll back the transaction, preserving data consistency.