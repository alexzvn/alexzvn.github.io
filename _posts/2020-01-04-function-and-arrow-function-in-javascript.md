---
layout: post
title: "function và arrow function trong javascript"
categories: programing
tags: javascript language
---

Trong 1 lần xây dựng layout bằng Vue, có mội lỗi mà tui mất hàng tiếng đồng hồ để gỡ lỗi. Một trong số đó liên quan đến function và arrow function. Lấy ví dụ như một đoạn code dưới đây, nó thực hiện mỗi khi người dùng nhập dữ liệu.

```js
export default {
  data () {
    return { code: '' }
  },

  watch: {
    code: () => {
      this.lookupDatabase() // this === undefined
    }
  },

  methods: {
    lookupDatabase () {
      // lookup database
    }
  }
}
```

Tốn một hồi lâu trên mạng thì cuối cùng cũng tìm được lời giải tại [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions). Về cơ bản thì nó giải thích như sau. `Arrow function` là bản rút gọn của `function` truyền thống. Thế nên cũng có một số cái giới hạn và khác nhau giữa 2 thằng này. Ví dụ như trong tài liệu nói:

- Nó không có sự ràng buộc `this` hoặc `super` của chính function đó. Và không nên dùng dưới dạng `method`
- Không có từ khóa `arguments` hoặc `new.target`
- Không thích hợp cho `call`, `apply` và `bind` method
- Không thể sử dụng như một `constructors`.
- Không dùng được từ khóa yield trong `arrow function`

Theo như trên thì ta phải viết lại cho đúng.
```js
...
  watch: {
    code: function () {
      this.lookupDatabase() // problem solved
    }
  },
...
```

Rút gọn lại, hãy dùng `arrow function` như một closure/anonymous function. Còn để xây dựng method cho một object thì hãy dùng `function` truyền thống 🐒.

~~It's not like i like javascript or anything baka.~~
