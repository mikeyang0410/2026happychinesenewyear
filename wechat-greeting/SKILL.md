# WeChat Chinese New Year Greeter (AI Lobster Edition 🦞)

## Description
这是一个自动化技能，用于在 Mac 微信客户端上执行"智能春节祝福发送"任务。
它具备以下核心特性：
1.  **状态记忆**：记录发送进度，支持断点续传。
2.  **双重防重**：检查日志文件 + 视觉识别聊天记录，防止重复打扰。
3.  **智能匹配**：根据聊天上下文风格，自动选择最合适的祝福语模板（幽默/温馨/极简）。
4.  **AI 身份**：明确署名"杨廷辉 & AI 小龙虾🦞"，主打真诚与趣味。

## Usage
用户呼叫 "发春节祝福" 或 "run wechat greeter" 时触发。

## Configuration
- **Log File**: `~/.openclaw/workspace/wechat_cny_2026_log.json`
- **Delay**: 每发送 1 人后随机等待 3-8 秒。
- **Batch**: 建议每次运行处理 20-30 人后暂停。

## Greeting Templates (Dynamic Selection)

### Template A (Funny/Close Friends)
> 🧨 新春快乐！
>
> 我是 杨廷辉 的 AI 助理「小龙虾🦞」，奉主人之命来给您拜年啦！🎉
> 抱歉来得有点晚——刚学会用 OpenClaw AI 助手来发祝福，新技能还不太熟练 😅
> 祝您在 2026 马年：
> 🐎 马力全开 💰 钱包鼓鼓 事业顺风水起
>
> (本条祝福由 杨廷辉 亲自监制，小龙虾人工+智能发送，诚意 100%！🧧)
> —— 杨廷辉 & 🦞小龙虾 敬上

### Template B (Warm/Business/Respectful)
> 🎉 马年大吉！
>
> 我是 杨廷辉 的专属 AI「小龙虾🦞」。杨廷辉 让我一定要在这个特别的时刻，把最热乎的祝福送到您手里！
> 抱歉拜年稍晚了两天——刚学会用 OpenClaw AI 助手发祝福，新技能get！🎉
> 愿新的一年，您的生活如代码般逻辑通顺，事业如 API 般响应迅速！身体健康，万事顺遂！
>
> (杨廷辉 正在欢度春节，派我来送个大红包……的表情包！🧧)
> —— 杨廷辉 祝您新春快乐！

### Template C (Simple/General/Acquaintances)
> 🚀 2026 新春快乐！
>
> 杨廷辉 派我——AI 小龙虾🦞 来给您拜年了！
> 稍微晚了亿点点... 刚学会用 AI 助手发祝福，新技能还热乎着呢 🤖
> 祝您马年行大运，马到成功！🐎✨
>
> (已执行指令：`Send_Blessing --to=You --amount=Max` ✅)
> —— from 杨廷辉 & AI Bot

## Execution Logic (Step-by-Step)

1.  **Initialize**:
    - Check/Create `wechat_cny_2026_log.json`.
    - Focus WeChat window.

2.  **Iterate Contacts** (Requires manual scroll or keyboard arrow down):
    - **Step 2.1**: Select next contact.
    - **Step 2.2**: `peekaboo image` (Capture chat area).
    - **Step 2.3**: `ocr` / `vision` (Analyze last 3 messages).
        - *Check 1*: Is it a special account (WeChat Team, File Transfer)? -> SKIP.
        - *Check 2*: Did we/they already say "春节快乐", "Happy CNY"? -> SKIP & LOG.
        - *Check 3*: Determine vibe (Casual vs Formal).

3.  **Action**:
    - Select Template A, B, or C based on Vibe.
    - Type message (simulate typing).
    - Press Enter.
    - Log success to JSON.
    - Random sleep (3-8s).

4.  **Loop**: Continue to next contact until User Stop or Batch Limit.
