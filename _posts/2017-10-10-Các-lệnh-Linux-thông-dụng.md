---
title: "Các lệnh thông dụng và hữu ích khi làm việc với Linux và OpenFOAM"
sub_title: "Useful command line when working with Linux and OpenFOAM"
categories:
  - Command Line
  - Linux
  - OpenFoam
elements:
  - css
  - formatting
  - html
  - markup
last_modified_at: 2017-10-10T11:23:59-12:00
---
Bài viết này tập hợp các lệnh thông dụng và hữu ích khi làm việc với <kbd>Linux</kbd> và <kbd>OpenFOAM</kbd>.

### 1. Linux
1.1 Các lệnh điều hướng:
* <kbd> pwd </kbd>    : Hiển thị tên thư mục đang làm việc
* <kbd> ls </kbd>     : Hiển thị các thư mục và file có trong thư mục hiện tại
* <kbd> cd </kbd>     : Chuyển tới thư mục mới
    * <kbd> cd .. </kbd>: Trở về 1 thư mục trước

1.2 Các lệnh hiển thị

* <kbd> cat </kbd>     : Hiển thị nội dung chỉ định trong 1 file, có nhiều lựa chọn đi kèm.
* <kbd> tail </kbd>   : Hiện thị dòng cuối cùng trong văn bản, có nhiều lựa chọn đi kèm.

1.3 Các lệnh làm việc với file

* <kbd> cp </kbd>     : Copy một hoặc nhiều files, option **-r** để copy thư mục
* <kbd> mkdir </kbd>  : Tạo một folder mới
* <kbd> rm </kbd>     : Xóa file. Option **-r** để xóa thư mục.
* <kbd> mv </kbd>     : Di chuyển hoặc sửa tên file/thư mục

1.4 Các lệnh hữu ích khác

* <kbd> PS1='\u:\W\$ ' </kbd> : Rút gọn đường dẫn hiển thị ở command line. Thông tin chi tiết hơn có thể xem [tại đây](http://www.linuxselfhelp.com/howtos/Bash-Prompt/Bash-Prompt-HOWTO-2.html)
    * Example
        ```bash
        root@root:/a/b/c/d/e$ PS1='\u:\W\$ '
        root@root:e$
        ```


### 2. OpenFOAM

Being updated ...