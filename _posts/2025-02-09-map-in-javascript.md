---
created: 2025-02-10
title: 대댓글 활용에서의 map 함수 (javascript)
tags: [javasciprt, map, map함수, 댓글, 대댓글, comments, tree, 트리구조]
category: javascript
image: assets/img/category/javascript.png
---

# 🚀 **JavaScript의 Map과 객체 참조 개념**

## 🔍 **Map 객체의 특징**
- **Key-Value 구조**: `key`를 기준으로 데이터를 저장하고 검색할 수 있음.
- **객체보다 성능 우수**: 일반적인 객체 `{}` 를 이용한 키-값 저장보다 `Map`은 검색과 조회 성능이 뛰어남.
- **Key에 다양한 타입 가능**: 객체의 키는 문자열만 가능하지만, `Map`은 `string`, `number`, `object` 등 다양한 타입을 key로 사용할 수 있음.

---

## 🔥 **Map을 사용한 댓글 트리 구조 생성**

```typescript
const commentMap = new Map();
const rootComments: any[] = [];

comments.forEach((comment) => {
  comment.children = []; // 댓글 객체에 children 속성 추가
  commentMap.set(comment.id, comment); // 댓글 ID를 key로, 댓글 객체를 value로 저장

  if (comment.parentId) { // 부모 댓글이 있는 경우
    const parent = commentMap.get(comment.parentId); // 부모 댓글 찾기
    if (parent) {
      parent.children.push(comment); // 부모 댓글의 children 배열에 추가
    }
  } else {
    rootComments.push(comment); // 최상위 댓글이면 rootComments에 추가
  }
});
```

