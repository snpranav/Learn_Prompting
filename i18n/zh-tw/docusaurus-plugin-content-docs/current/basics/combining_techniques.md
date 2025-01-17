---
sidebar_position: 80
locale: zh-Hans
style: chicago
---

# 🟢 組合提示

import CombinedPrompt from '@site/docs/assets/basics/combined_prompt.svg';

<div style={{textAlign: 'center'}}>
  <CombinedPrompt style={{width:"500px",height:"300px",verticalAlign:"top"}}/>
</div>

:::takeaways
- 了解如何結合不同的提示技巧
:::

正如我們在前面的教程中所看到的，面向模型的提示具有不同的格式和其複雜性。它們可以包括 **上下文**、**指令式的提示詞** 和 **多個輸入-輸出** 的範例。然而，到目前為止，我們只研究了獨立的提示類別。將這些不同的技巧組合起來可以產生更強大的提示。

以下是一個包含上下文、指令以及多範例提示的例子：

```text
Twitter是一個社交媒體平臺，使用者可以釋出稱為“推文”的短訊息。推文可以是積極的或消極的，我們希望能夠將推文分類為積極或消極。以下是一些積極和消極推文的例子。請確保正確分類最後一個推文。

Q: 推文: "今天真是美好的一天！"
這條推文是積極的還是消極的？

A: 積極的

Q: 推文: 我討厭這個班級"
這條推文是積極的還是消極的？

A: 消極的

Q: 推文: "我喜歡牛仔褲上的口袋"

A:
```

透過新增額外的上下文和範例，我們通常可以提高人工智慧在不同任務上的表現。

By [gezilinll](https://github.com/gezilinll).
