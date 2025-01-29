# Uncontrolled Component Updates: Missing Cleanup in useEffect with setInterval

This repository demonstrates a common bug in React components involving the `useEffect` hook and `setInterval`.  The bug arises from a missing cleanup function to stop the interval when the component unmounts or updates. This leads to uncontrolled component updates and potential memory leaks.

## Bug Description

The `MyComponent` attempts to update a counter every second using `setInterval`. However, it lacks a cleanup function within `useEffect` to clear the interval (`clearInterval`). This means that even when the component unmounts, the interval continues to run, causing unexpected behavior.

## Solution

The solution involves returning a cleanup function from `useEffect`.  This function is called when the component unmounts or when the dependencies array changes. The cleanup function should clear the interval using `clearInterval`, ensuring the interval is properly stopped.

## How to reproduce the bug:

1. Clone the repository.
2. Run `npm install` to install dependencies.
3. Run `npm start` to start the development server.
4. Observe the counter continuously increasing even after navigating away from the component. This indicates a memory leak and uncontrolled updates.
