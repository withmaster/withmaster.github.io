# notion을 이용해서 github로 포스팅하기

Created: 2021년 12월 14일 오후 10:15
Posting: No

## Why?

- github 블로그를 이용하면, markdown(*.md)을 이용해서 포스팅 해야 합니다.
- 마크다운을 바로 작성하는 것은 귀찮은 일이기 때문에 보통 주피터 노트북이나 Visual studio code와 같은 Editor를 이용합니다. 하지만, 이것도 꽤 귀찮은 일이죠.
- notion은 뛰어난 편집 기능을 제공하고 있는데, markdown 포맷을 내보내기를 지원하고 있으니 활용해 보아야겠죠.

## How?

1. 준비물
    - github 블로그
    - notion 계정
2. 노션에서 글 작성하기
3. 마크다운 파일로 내보내기
    - `…` 선택하고, 내보내기(export) 선택
    
    ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-notion_to_github/Untitled.png)
    
    - 내보내기 형식으로 `Markdown & CSV`를 선택합니다.
    - 내보내기를 클릭하면, 문서 폴더(선택 가능)에 Export-xxxxx.zip 파일이 저장됩니다.
        
        ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-notion_to_github/Untitled%201.png)
        
4. 압축을 해제하면  아래와 같이 image 폴더와 마크 다운 파일(md)이 생성됩니다.
    
    ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-notion_to_github/Untitled%202.png)
    
5. 폴더명 및 파일명 수정하기
    - 폴더명 및 파일명은 각자의 naming rule에 따라 설정하면 됩니다만, github 블로그의 경우 보통 `yyyy-mm-dd-title` 형태로 많이 사용하므로 포스팅 날짜 기준으로 2021-12-14-notion_to_github로 둘 다 변경하였습니다.
        
        ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-notion_to_github/Untitled%203.png)
        
6. 이미지 폴더 업로드 하기
    - 2021-12-14-notion_to_github 폴더를 내 컴퓨터에서 블로그를 github 블로그를 관리하는 폴더 아래에 있는 assests 폴더로 옮깁니다.
    - 참고로 github에 용량 제한이 있긴 하지만, notion에서 내보내기를 하면 이미지 하나당 100kb정도로 조정하기 때문에 크게 신경쓰지 않아도 됩니다.
        
        ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-notion_to_github/Untitled%204.png)
        
    - command line에서 아래 코드들을 순서대로 입력하면, image 파일들이 업로드 됩니다.
        
        ```python
        git add .
        git commit -m "2021-12-14-notion_to_github - upload image"
        git push -u origin master
        ```
        
7. 마크다운 파일(*.md) 수정하기
    - VSC(Visual Studio Code)에서 미리보기가 가능하므로, VSC를 에디터로 사용합니다.
    - YFM 추가하기
        - YFM은 YAML Front Matter라고 하여 오픈 소스 프로젝트에서 많이 사용하는 구조화된 데이터 형식입니다.
        - markdown파일의 최상단에 위치하며 3개의 하이픈(`--` )으로 시작과 끝을 나타냅니다.
        - 예시
            
            ```markdown
            ---
              title:  "포스트 상단 및 글 제목에 노출되는 제목입니다."
              excerpt: "제목 하단에 표시되며, 포스팅 내용을 1줄로 작성하면 됩니다."
            
              categories:
                - 블로그
              tags:
                - github
                - notion
                - tip
            
              toc: true
              toc_sticky: true
              toc_label: "페이지 주요 목차"
              ---
            ```
            
        - categories
            - 블로그 카테고리는 게시물을 제목이나 유형으로 분류할 때 사용되며, 블로그에 대한 일반적인 주제를 글 묶음을 위해 사용됩니다.
        - tag
            - 태그는 해당 게시물의 세부 정보를 키워드로 설명하는 것이며, 해시태그와 유사한 것으로 볼 수 있다.
        - TOC(Table of Contents)
            - 목차 기능으로 마크다운 생성시 `#`을 이용하여 생성한 내용들이 표시됩니다.
            - `toc: true`는 목차를 사용하겠다는 의미이고,
            - `toc_sticky: true`는 목차의 위치를 고정하겠다는 의미입니다.
            - `toc_label`는 목차의 제목을 의미합니다.
        - YFM 추가 결과
            
            ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-notion_to_github/Untitled%205.png)
            
    - 이미지 파일 링크 수정하기
        - 이미지 파일의 링크를 notion을 기준으로 생성되기 때문에 github를 기준으로 변경해주어야 합니다.
        - 
        - 변경 전
            
            ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-notion_to_github/Untitled%206.png)
            
        - 변경 후
            
            ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-notion_to_github/Untitled%207.png)
            
        - 위에서 assets/images 폴더 아래에 2021-12-14-notion_to_github폴더를 에 넣어주었으므로 실제 경로는 `https://my_account.github.io/assets/images/2021-12-14-notion_to_github/Untilted.png` 가 됩니다.
        - 여기서 `my_account`는 본인의 계정명입니다.
        - 따라서 맨 끝에 `/Untilted.png`나  `/Untilted%201.png`는 제외한 (`notion~` )부분을 찾아서 `https://my_account.github.io/assets/images/2021-12-14-notion_to_github`로 바꾸기(Ctrl+h)로 변경하면 됩니다.
        - 제대로 변경이 되면 미리보기로 image를 확인할 수 있습니다.
            
            ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-notion_to_github/Untitled%208.png)
            
    - 수정한 마크 다운 파일을 `_posts`폴더에 옮기고, 업로드하기
        
        ```python
        git add .
        git commit -m "2021-12-14-notion_to_github - upload markdown"
        git push -u origin master
        ```
        

## 마치며

- 이미지 파일이 없거나 YFM을 사용하지 않는다면 마크 다운 파일을 수정할 일이 없어서 내보내기한 파일을 바로 업로드 해도 됩니다.
- 저 같은 경우에는 이전에 업로드한 마크 다운 파일에서 YFM을 복사해서 붙여넣고, 이미지 파일의 경로는 찾아 바꾸기(ctrl + h)로 한번에 변경할 수 있으므로 익숙해지면, 한 번 업로드로 끝낼 수 있어서 시간이 오래 걸리진 않습니다.
- 옮기는 과정이 귀찮긴 하지만, notion의 편집 기능이 워낙 훌륭하기 때문에 이 정도 단점은 충분히 상쇄한다고 생각합니다.