# React Native useEffect Cleanup Issue with Async Operations

This repository demonstrates a common issue in React Native where the cleanup function within the `useEffect` hook doesn't execute correctly when dealing with asynchronous operations.  If the component unmounts before the asynchronous task completes, the cleanup function is skipped, potentially leading to memory leaks or other problems.

## Problem
The `bug.js` file showcases the problem: An asynchronous operation (e.g., a network request) is performed within `useEffect`.  If the component is unmounted before the `fetch` call resolves, the cleanup function responsible for canceling the request or cleaning up resources is never invoked.

## Solution
The `bugSolution.js` file presents a solution. By using a flag to track whether the component is still mounted, we can prevent the cleanup function from executing unnecessary operations after the component has been unmounted.