# Git-Flow

## 1. Branch organization:

  * master: Branch có mục đích sử dụng cho môi trường Production.
  * develop: Branch có mục đich sử dụng cho môi trường Development. Các branch feature sẽ được tạo từ đây
  * release: Branch có mục đích chuẩn bị môi trường cho những branch feature, fix-bug sẵn sàng lên production
  
## 2. feature branch:

  * Tạo branch từ develop

    > git checkout -b feature_name develop
    
  * Sau khi develop & UT, tạo Pull request & review assign vào branch develop
  
## 3. release branch:

  * Tạo branch từ develop
  
    > git checkout -b release-X.X.X develop
    
  * (Suggestion) Tạo Changelog cho Project: Mình có 1 file bump-version.sh(file này mình tham khảo, có source trong file) giúp tự động quá trình này
  
    > sh bump-version.sh
    
    [![bump-version.sh Result](https://s17.postimg.org/lz990qvb3/Capture.png)](https://postimg.org/image/pvmkwqgaj/)
    
  * Tạo Pull request & assign branch vào master
  
  * Merge branch release lại develop để đồng bộ quá trình bump-version or...
  
    > git checkout develop
    
    > git merge --no-ff release-X.X.X
    
## 4. hot-fix branch:

  * Tạo branch từ master:
  
    > git checkout -b hot-fix_name master
    
  * Sau khi develop & UT, update version:
  
    > sh bump-version.sh
    
  * Tạo PR & assign review vào master
  
  * Merge branch hot-fix vào develop để tránh thiếu code:
    
    > git checkout develop
    
    > git merge --no-ff hot-fix_name
    
    
![Git tree(http://nvie.com/img/git-model@2x.png)](http://nvie.com/img/git-model@2x.png)

Source: http://nvie.com/posts/a-successful-git-branching-model/
  
  
  

    
    
  
