---
title: "useEffect Hook"
date: 2022-08-23T07:52:58+07:00
draft: true
description: "Tìm hiểu useEffect Hook"
summary: "Tìm hiểu useEffect Hook"
tags:
- useEffect Hook
- Hook
- React
- Tự học React
---

> Effect hook cho phép thực hiện side effect bên trong các function component.
>
>> Side effect là một chương trình phần mềm khi có tác động xảy ra nó làm thay đổi dữ liệu phần mềm, thuật ngữ sử dụng chung trong lĩnh vực lập trình phần mềm.

## 1. useEffect hook dùng để làm gì?

- Update DOM
- Call API
- Listen DOM events
  - Scroll
  - Resize
- Cleanup
  - Remove listener / Unsubscribe
  - Clear timer

## 2. Các ví dụ trường hợp về useEffect hook

- Callback luôn được gọi sau khi component mounted
- Cleanup function luôn được gọi trước khi component unmounted
- Cleanup function luôn được gọi trước khi callback được gọi (trừ lần mounted)
- Có 3 kiểu cấu trúc của useEffect:

    > #### useEffect(callback)
    >
    > - Gọi callback mỗi khi component re-render
    > - Gọi callback sau khi component thêm element vào DOM

    ```jsx
    import { useEffect, useState } from "react";

    const Content = () => {
    const [title, setTitle] = useState("");

    useEffect(() => {
        document.title = title;
        });
    return (
    <div>
      <input value={title} onChange={(e) => setTitle(e.target.value)} />
    </div>
        );
    };

    export default Content;

    ```

    > #### useEffect(callback, [])
    >
    > - Chỉ gọi callback 1 lần sau khi component mounted

    ```jsx
    import { useEffect, useState } from "react";

    const Content = () => {
    const [posts, setPosts] = useState([]);

    useEffect(() => {
        fetch("https://jsonplaceholder.typicode.com/posts")
            .then((res) => res.json())
            .then((posts) => {
                setPosts(posts);
            });
        }, []);

    return (
        <div>
            <input value={title} onChange={(e) => setTitle(e.target.value)} />
            <ul>
            {posts.map((post) => (
                <li key={post.id}>{post.title}</li>
            ))}
             </ul>
        </div>
        );
    };

    export default Content;

    ```

    > #### useEffect(callback, [deps])
    >
    > - `deps` là một cái biến chứa giá trị dữ liệu
    > - Callback sẽ được gọi lại mỗi khi `deps` thay đổi.

    ```jsx
    import { useEffect, useState } from "react";

    const tabs = ["posts", "comments", "albums", "todos", "users"];

    const Content = () => {
    const [posts, setPosts] = useState([]);
    const [type, setType] = useState("posts");

    useEffect(() => {
        fetch(`https://jsonplaceholder.typicode.com/${type}`)
            .then((res) => res.json())
            .then((posts) => {
                setPosts(posts);
            });
         }, [type]);

    return (
        <div>
        {tabs.map((tab, index) => (
            <button
            key={index}
            onClick={() => setType(tab)}
            style={type === tab ? { color: "white", background: "pink" } : {}}
            >
            {tab}
            </button>
            ))}
            <ul>
            {posts.map((post) => (
                <li key={post.id}>{post.title || post.name}</li>
            ))}
            </ul>
        </div>
         );
    };

    export default Content;

    ```

## 3. useEffect with DOM events

```jsx
import { useEffect, useState } from "react";

const tabs = ["posts", "comments", "albums", "todos", "users"];
const Content = () => {
  const [posts, setPosts] = useState([]);
  const [type, setType] = useState("posts");
  const [showGoToTop, setShowGoToTop] = useState(false);

  useEffect(() => {
    fetch(`https://jsonplaceholder.typicode.com/${type}`)
      .then((res) => res.json())
      .then((posts) => {
        setPosts(posts);
      });
  }, [type]);

  useEffect(() => {
    const handleScroll = () => {
      if (window.scrollY >= 200) {
        setShowGoToTop(true);
      } else {
        setShowGoToTop(false);
      }
    };
    window.addEventListener("scroll", handleScroll);
    return () => {
      window.removeEventListener("scroll", handleScroll);
    };
  }, []);

  return (
    <div>
      {tabs.map((tab, index) => (
        <button
          key={index}
          onClick={() => setType(tab)}
          style={type === tab ? { color: "white", background: "pink" } : {}}
        >
          {tab}
        </button>
      ))}
      <ul>
        {posts.map((post) => (
          <li key={post.id}>{post.title || post.name}</li>
        ))}
        {showGoToTop && (
          <button
            style={{
              position: "fixed",
              right: 20,
              bottom: 20,
            }}
          >
            Go to Top
          </button>
        )}
      </ul>
    </div>
  );
};

export default Content;

```

## 4. useEffect with timer functions

> Với setInterval()

```jsx
import { useEffect, useState } from "react";

const Content = () => {
  const [countdown, setCountdown] = useState(180);

  useEffect(() => {
    const timerId = setInterval(() => {
      setCountdown((prevState) => prevState - 1);
    }, 1000);

    return () => clearInterval(timerId);
  }, []);

  return (
    <div>
      <h1>{countdown}</h1>
    </div>
  );
};

export default Content;

```

> Với setTimeout()

```jsx
import { useEffect, useState } from "react";

const Content = () => {
  const [countdown, setCountdown] = useState(180);

  useEffect(() => {
    setTimeout(() => {
      setCountdown(countdown - 1);
    }, 1000);
  }, [countdown]);

  return (
    <div>
      <h1>{countdown}</h1>
    </div>
  );
};

export default Content;

```

## 5. useEffect with preview avatar

```jsx
import { useEffect, useState } from "react";

const Content = () => {
  const [avatar, setAvatar] = useState();

  useEffect(() => {
    return () => {
      // Tránh việc ảnh bị rò rỉ ra bên ngoài
      avatar && URL.revokeObjectURL(avatar.preview);
    };
  }, [avatar]);

  const handlePreviewAvatar = (e) => {
    const file = e.target.files[0];

    file.preview = URL.createObjectURL(file);

    setAvatar(file);
  };
  return (
    <div>
      <input type="file" onChange={handlePreviewAvatar} />
      {avatar && <img src={avatar.preview} alt="" width="80%" />}
    </div>
  );
};

export default Content;

```

## 6. useEffect with fake Chat App

