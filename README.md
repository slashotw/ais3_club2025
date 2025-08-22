# ais3_club2025

## slide
[https://github.com/slashotw/ais3_club2025/blob/main/ais3club2025.pdf](https://github.com/slashotw/ais3_club2025/blob/main/ais3club2025.pdf)
## slido 
[https://app.sli.do/event/hd24gwxMrU14f6fzFbji4T](https://app.sli.do/event/hd24gwxMrU14f6fzFbji4T)
## tldraw 
[https://www.tldraw.com/f/u3agNbkgT5Ucsn9uDpTQR?d=v-861.-1156.3248.2039.E0B0_fdPUIVC22Unf2DqY](https://www.tldraw.com/f/u3agNbkgT5Ucsn9uDpTQR?d=v-861.-1156.3248.2039.E0B0_fdPUIVC22Unf2DqY)

## n8n 
#### google sheet 模板
[https://docs.google.com/spreadsheets/d/1zwCBpH9ipX_mMcY69jrWlWEw9TaMbB4lnyy3MWg5QPI/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1zwCBpH9ipX_mMcY69jrWlWEw9TaMbB4lnyy3MWg5QPI/edit?usp=sharing)

#### code node模板
```
const principal = Number($json["欠款金額"]);
const startDate = new Date("2025-08-01"); // 設定應繳日期
const daysLate = Math.max(0, Math.floor((Date.now() - startDate) / (1000 * 60 * 60 * 24)));
const interestRate = 0.01; // 每日1%利息
const interest = Math.floor(principal * interestRate * daysLate);
const total = principal + interest;

// 把 prompt 組裝好，交給 OpenAI Node
const prompt = `
以下是一個「ais3資安研究社」的社費欠繳人的資訊。
請幫我生成一封帶有極具情緒勒索特色的 Email 「內文」，內容包含：
- 收件人：${$json["姓名"]}
- 原始社費：NT$${principal}
- 已逾天數：${daysLate} 天
- 當前利息：NT$${interest}
- 總計需繳：NT$${total}
'
備註：請直接生成內容 不需要解釋的輔助文字
`;

return {
  姓名: $json["姓名"],
  Email: $json["Email"],
  欠款金額: principal,
  已逾天數: daysLate,
  利息: interest,
  總額: total,
  prompt: prompt
};
```
