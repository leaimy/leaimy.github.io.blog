---
title: "Two-way Binding"
date: 2022-08-22T10:49:03+07:00
draft: true
description: "Two-way binding trong React?"
summary: "Two-way binding trong React?"
tags:
- Tow-way binding
- useState hook
- Hook
- React
- Tự học React
---

> React mặc định là one-way binding (ràng buộc một chiều), two-way binding là ràng buộc dữ liệu 2 chiều, điều này thường được nhắc tới khi làm việc với biểu mẫu (form) trong các lib/framework front-end.

## 1. Two-way binding là gì?

- Dữ liệu chúng ta thay đổi trong giao diện sẽ được cập nhật trong trạng thái.
- Dữ liệu trong state sẽ được cập nhật lại trong giao diện.

![two-way](/images/twobinding.png)

## 2. Two-way binding trong React hooks

```jsx
import { useState } from "react";

function App() {
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");

  const handleSubmit = () => {
    console.log({
      name,
      email,
    });
  };

  return (
    <div className="App" style={{ padding: "20px" }}>
      <input value={name} onChange={(e) => setName(e.target.value)} />
      <input value={email} onChange={(e) => setEmail(e.target.value)} />
      <button onClick={handleSubmit}>Register</button>
    </div>
  );
}

export default App;
```

## 3. Một số ứng dụng two-way binding

***Ví dụ 1:*** Ứng dụng trong Radio Button

```jsx
import { useState } from "react";

const courses = [
  {
    id: 1,
    name: "HTML, CSS",
  },
  {
    id: 2,
    name: "Javascript",
  },
  {
    id: 3,
    name: "ReactJS",
  },
];
function App() {
  const [checked, setChecked] = useState(2);
  const handleSubmit = () => {
    // Call API
    console.log({ id: checked });
  };

  return (
    <div className="App" style={{ padding: "40px" }}>
      {courses.map((course) => (
        <div key={course.id}>
          <input
            type="radio"
            checked={checked === course.id}
            onChange={() => setChecked(course.id)}
          />
          {course.name}
        </div>
      ))}

      <button onClick={handleSubmit}>Register</button>
    </div>
  );
}

export default App;

```

***Ví dụ 2:*** Ứng dụng trong Checkbox

```jsx
import { useState } from "react";

const courses = [
  {
    id: 1,
    name: "HTML, CSS",
  },
  {
    id: 2,
    name: "Javascript",
  },
  {
    id: 3,
    name: "ReactJS",
  },
];
function App() {
  const [checked, setChecked] = useState([]);
  console.log(checked);

  const handleCheck = (id) => {
    setChecked((prev) => {
      const isChecked = checked.includes(id);
      if (isChecked) {
        return checked.filter((item) => item !== id);
      } else {
        return [...prev, id];
      }
    });
  };

  const handleSubmit = () => {
    // Call API
    console.log({ id: checked });
  };

  return (
    <div className="App" style={{ padding: "40px" }}>
      {courses.map((course) => (
        <div key={course.id}>
          <input
            type="checkbox"
            checked={checked.includes(course.id)}
            onChange={() => handleCheck(course.id)}
          />
          {course.name}
        </div>
      ))}

      <button onClick={handleSubmit}>Register</button>
    </div>
  );
}

export default App;

```

## 4. Todolist with useState

```jsx
import { useState } from "react";

function App() {
  const [job, setJob] = useState("");
  const [jobs, setJobs] = useState(() => {
    const storageJobs = JSON.parse(localStorage.getItem("jobs"));

    return storageJobs ?? [];
  });

  const handleDelete = (job) => {
    const newJobs = jobs.filter((todo) => {
      return todo != job;
    });

    setJobs(newJobs);
    window.localStorage.setItem("jobs", JSON.stringify(newJobs));
  };

  const handleAdd = () => {
    setJobs((prev) => {
      const newJobs = [...prev, job];

      // Lưu vào local storage
      const jsonJobs = JSON.stringify(newJobs);
      localStorage.setItem("jobs", jsonJobs);

      return newJobs;
    });

    setJob("");
  };

  return (
    <div className="App" style={{ padding: "40px" }}>
      <input
        value={job}
        style={{ margin: "10px" }}
        onChange={(e) => setJob(e.target.value)}
      />
      <button onClick={handleAdd}>Thêm</button>

      <ul>
        {jobs.map((job, index) => {
          return (
            <>
              <li key={index}>
                {job}{" "}
                <button
                  onClick={() => handleDelete(job)}
                  style={{ color: "red" }}
                >
                  X
                </button>
              </li>
            </>
          );
        })}
      </ul>
    </div>
  );
}

export default App;

```

