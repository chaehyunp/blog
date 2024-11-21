### 🚨 문제 상황
<img width="260" alt="스크린샷 2024-11-21 오후 7 55 14" src="https://github.com/user-attachments/assets/a283a6be-22ac-41d9-9b7b-893f1444c0cd">

프로젝트를 들어가려고 하는데 프로젝트 파일이 손상되어 열 수 없다고 했다. 방금까지 잘 수정했는데 황당할 노릇이었다.

</br>

---

</br>

### 👏 문제 해결
[The project ‘project’ is damaged and cannot be opened due to a parse error.](https://stackoverflow.com/questions/62561644/the-project-project-is-damaged-and-cannot-be-opened-due-to-a-parse-error-exam)

<img width="600" alt="스크린샷 2024-11-21 오후 9 29 48" src="https://github.com/user-attachments/assets/e156ab2e-63e7-44d8-901f-1f54ad06b777">

찾아보니 ***프로젝트 파일에 깃 컨플릭트에 대한 괄호가 있어서 안된다***는 내용이 스택오버플로우에 있었다.

<img width="600" alt="스크린샷 2024-11-21 오후 9 34 16" src="https://github.com/user-attachments/assets/c1c237e3-f7fc-479e-8b98-06e85bfd9315">

VSCode를 켜서 열어보니 괄호가 참 많이 있었다... 푸시를 하려다가 스태시 하겠냐는 모달이 떴었는데 그것때문인가...

다 지우니까 잘 작동됐다.
