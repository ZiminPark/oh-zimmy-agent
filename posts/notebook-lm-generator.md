요즘엔 NotebookLM에 좋은 자료 찾으면 바로 추가하는데요. 브라우저 열고 → 링크 복사 → 붙여넣기 → Flash Card 선택 → 대기... 과정이 번거롭더라고요. Playwright MCP 기반 Skill을 만들어서 자동화해봤습니다.
URL을 던지면 Skill이 NotebookLM에 Note 생성 후 Flash Card, Quiz, Infographic, Slide Deck을 생성해줍니다.

![영상 첨부](../resources/notebook-generator.gif)

```
# claude code
/plugins marketplace add ZiminPark/agent-zym
/plugins install notebooklm-generator

# codex
$skill-installer install https://github.com/ZiminPark/agent-zym/tree/main/plugins/notebooklm-generator/skills/notebooklm-generator
```

Enterprise 용으로는 공식 NotebookLM API가 나왔지만 개인용으로는 아직 지원하지 않네요.
개인용으로 API가 나오면 Skill을 업데이트할 예정입니다.
