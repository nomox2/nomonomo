# 피그마 MCP 색상 변경 설정 가이드 / Figma MCP Color Change Setup Guide

## 문제 상황 / Issue
피그마에서 색상이 바뀌지 않는 이유는 전체 시스템이 아직 설정되지 않았기 때문입니다.
The color didn't change in Figma because the complete system isn't set up yet.

## 필요한 설정 단계 / Required Setup Steps

### 1. WebSocket 서버 시작 / Start WebSocket Server
```bash
# 새 터미널에서 실행 / Run in new terminal
bunx cursor-talk-to-figma-plugin@latest
```

### 2. 피그마 플러그인 설치 / Install Figma Plugin
1. 피그마에서 Plugins > Development > New Plugin으로 이동
2. "Link existing plugin" 선택  
3. 플러그인 매니페스트 파일을 찾아서 링크
4. 플러그인을 실행하고 채널에 연결

### 3. 실제 색상 변경 명령 / Actual Color Change Commands

#### 피그마에서 실행할 단계 / Steps to execute in Figma:

1. **요소 선택** / **Select Elements**: 색상을 변경하고자 하는 피그마의 요소들을 선택합니다.

2. **Cursor에서 다음 명령 사용** / **Use these commands in Cursor**:
```
현재 선택된 요소들의 색상을 #FFE661에서 #FFE501로 변경해줘
```
또는
```
Change the fill color of selected elements from #FFE661 to #FFE501
```

### 4. MCP 도구를 직접 사용 / Direct MCP Tool Usage

피그마가 연결되면 다음 MCP 도구들을 사용할 수 있습니다:

#### 선택된 요소 정보 확인 / Check Selected Elements
- `get_selection` - 현재 선택된 요소들 확인
- `get_node_info` - 특정 노드의 세부 정보 확인

#### 색상 변경 / Color Change
- `set_fill_color` - 선택된 요소의 배경색 변경
- `set_stroke_color` - 선택된 요소의 테두리색 변경

## 색상 변환 정보 / Color Conversion Info

**변경 전 / From**: `#FFE661` 
- RGB: (255, 230, 97)
- Figma RGB: (1.0, 0.902, 0.380)

**변경 후 / To**: `#FFE501`
- RGB: (255, 229, 1) 
- Figma RGB: (1.0, 0.898, 0.004)

## 트러블슈팅 / Troubleshooting

### 연결 문제 / Connection Issues
1. WebSocket 서버가 실행 중인지 확인
2. 피그마 플러그인이 활성화되어 있는지 확인
3. 브라우저 콘솔에서 연결 에러 메시지 확인

### 색상이 여전히 바뀌지 않는 경우 / If colors still don't change
1. 피그마에서 요소가 올바르게 선택되었는지 확인
2. 선택된 요소가 실제로 `#FFE661` 색상을 사용하는지 확인
3. 요소가 컴포넌트 인스턴스인지 확인 (컴포넌트는 별도 처리 필요)

## 다음 단계 / Next Steps

1. **먼저 WebSocket 서버를 시작하세요**
2. **피그마를 열고 플러그인을 설치/실행하세요**  
3. **색상을 변경하고자 하는 요소를 선택하세요**
4. **Cursor에서 자연어로 색상 변경을 요청하세요**

완전한 설정이 완료되면 자연어 명령으로 피그마의 색상을 실시간으로 변경할 수 있습니다.