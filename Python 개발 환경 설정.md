# 가상 환경
```bash
python3 -m venv --prompt ${name} ${path}
source ${path}/bin/activate
```
- Package 간 충돌을 방지하고 독립된 개발 환경을 구성하기 위해 사용
- Code를 작성할 경로에 가상 환경을 구성
- `activate` 파일의 환경 변수 설정을 load 하는 것으로 적용 가능

# Jupyter
```bash
python3 -m pip install jupyterlab
jupyter lab
```
- Unit Test 또는 Code Snippet 실행을 위해 사용하는 도구
- 프로젝트 내 Notebook, Lab 개별 패키지로 구성
	- Notebook은 기초적인 UI와 기능을 지원하며 Block 단위 실행 지원
	- Lab은 Notebook의 기능 외에도 추가적인 플러그인과 기능 지원

```bash
source ${venv_path}/bin/activate
python3 -m pip install ipykernel

python3 -m ipykernel install --user --name ${env_name} --display-name ${display_name}
```
- Server 설정 후 각 가상 환경의 `ipykernel`을 추가해서 사용
	- 가상 환경의 `ipykernel`을 추가하면 서버에 설치되어 있지 않더라도 해당 가상환경에 설치된 패키지를 사용한 테스트가 가능

# Code Editor 설정
> vscode 기준
> 설치: [Visual Studio Code - Code Editing. Redefined](https://code.visualstudio.com/)

## 추천 설정
- _Python: Venv Folders_: 프로젝트 폴더를 열었을 때 자동으로 인식하는 Python 가상 환경 디렉토리 이름
	- 설정하면 import와 같이 가상 환경에만 적용되는 내용을 자동으로 Load
- _Editor: Font Family - D2Coding_: 추천 폰트
## 추천 Extensions
- Auto Reload, AutoScroll: 로그파일과 같이 지속적으로 갱신되는 파일을 열었을 때 자동으로 갱신되고 가장 밑으로 자동으로 스크롤
	- Log File Hilighter
- Better Comments: 주석을 남길 떄 여러 Hilight 적용 가능
- Output Colorizer: 출력에 Hilight 적
- Partial Diff: 부분만 선택해서 내용 차이 점검 가능
- Project Manager: 저장된 경로에 바로 접근 가능 
- Python, Pylance, Python Debugger: Python 기본 Extentions
- Random Everything: 난수 데이터 생성
- Sort Lines: 선택한 영역을 정렬 가능
- Error Lens: 에디터 영역에 에러 내용 표시



---
#python #in-workspace 