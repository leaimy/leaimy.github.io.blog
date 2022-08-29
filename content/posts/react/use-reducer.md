---
title: "useReducer Hook"
date: 2022-08-25T10:25:50+07:00
draft: true
description: "Tìm hiểu useReducer"
summary: "Tìm hiểu useReducer"
tags: 
- useReducer Hook
- Hook
- React
- Tự học React
---

> `useReducer` Hook tương tự như `useState` Hook
> `useReducer` cho phép tuỳ chỉnh logic trạng thái
> `useReducer` hữu ích trong trường hợp theo dõi nhiều trạng thái dựa trên logic phức tạp.
> `useReducer` cung cấp cho người dùng có thêm một sự lựa chọn để sử dụng state cho function component

## 1. Cú pháp

- useReducer Hook chấp nhận hai đối số.

> Cú pháp: useReducer( <reducer>, <initialState> )

- Hàm `reducer` chứa logic trạng thái tuỳ chỉnh
- `initialState` có thể là một giá trị đơn giản nhưng nói chung sẽ chứa một đối tượng.
- `useReducer` hook trả về một `state` hiện tại và một phương thức `dispatch`.

## 2. Ví dụ minh hoạ useReducer

Đây là một ví dụ về `useReducer`:

```jsx
import { useReducer } from "react";

// useState
// 1. Init state: 0
// 2. Actions: Up (state + 1) / Down(state - 1)

// useReducer
// 1. Init state: 0
// 2. Actions: Up (state + 1) / Down (state - 1)
// 3. Reducer
// 4. Dispatch

// Init state
const initState = 0;

// Actions
const UP_ACTION = "up";
const DOWN_ACTION = "down";

// Reducer
const reducer = (state, action) => {
  console.log("reducer running...");

  switch (action) {
    case UP_ACTION:
      return state + 1;
    case DOWN_ACTION:
      return state - 1;
    default:
      throw new Error("Invalid action");
  }
};

function App() {
  const [count, dispatch] = useReducer(reducer, initState);

  return (
    <div className="App" style={{ padding: "40px" }}>
      <h1>{count}</h1>
      <button onClick={() => dispatch(UP_ACTION)}>Up</button>
      <button onClick={() => dispatch(DOWN_ACTION)}>Down</button>
    </div>
  );
}

export default App;
```

## 3. Bài tập Todo dùng useReducer

```jsx
import { useReducer, useRef } from "react";

// useReducer
// 1. Init state

const initState = {
  job: "",
  jobs: [],
};

// 2. Actions
const SET_JOB = "set_job";
const ADD_JOB = "add_job";
const DELETE_JOB = "delete_job";

const setJob = (payload) => {
  return {
    type: SET_JOB,
    payload,
  };
};

const addJob = (payload) => {
  return {
    type: ADD_JOB,
    payload,
  };
};

const deleteJob = (payload) => {
  return {
    type: DELETE_JOB,
    payload,
  };
};

// 3. Reducer
const reducer = (state, action) => {
  console.log("Action: ", action);
  console.log("Prev state: ", state);

  let newState;

  switch (action.type) {
    case SET_JOB:
      newState = {
        ...state,
        job: action.payload,
      };
      break;

    case ADD_JOB:
      newState = {
        ...state,
        jobs: [...state.jobs, action.payload],
      };
      break;

    case DELETE_JOB:
      const newJobs = [...state.jobs];
      newJobs.splice(action.payload, 1);
      newState = {
        ...state,
        jobs: newJobs,
      };
      break;

    default:
      throw new Error("Invalid action");
  }

  console.log("New state: ", newState);

  return newState;
};

// 4. Dispatch

function App() {
  const [state, dispatch] = useReducer(reducer, initState);
  const { job, jobs } = state;
  const inputRef = useRef();

  const handleAdd = () => {
    dispatch(addJob(job));
    dispatch(setJob(""));
    inputRef.current.focus();
  };

  return (
    <div className="App" style={{ padding: "40px" }}>
      <h3>Todo</h3>
      <input
        ref={inputRef}
        value={job}
        placeholder="Nhập công việc..."
        onChange={(e) => {
          dispatch(setJob(e.target.value));
        }}
      />
      <button onClick={handleAdd}>Add</button>
      <ul>
        {jobs.map((job, index) => (
          <li key={index}>
            {job}
            <span
              style={{ cursor: "pointer" }}
              onClick={() => dispatch(deleteJob(index))}
            >
              &times;
            </span>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default App;

```