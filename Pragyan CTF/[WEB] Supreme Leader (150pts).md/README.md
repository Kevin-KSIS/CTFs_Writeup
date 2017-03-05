> Category: Web

> Challenge: Supreme Leader (150pts)

> Writer: Kevinlpd

> Team: KS.IS

[+] URL: <http://139.59.62.216/supreme_leader>

[+] Solution:
 - Như một thói quen, trưóc khi bắt đầu 1 challenge web mình thường mở burpsuite thần thánh lên để tiện debugs.
 - Vào trang nhìn thấy toàn màu vàng chói và mặt anh "Ủn" là thấy tức cười :D.
 - Điều đầu tiên mình làm là bắt đầu từ việc đơn giản nhất rồi từ từ nâng độ khó challenge lên để tránh nhận định quá cao độ khó của thách thức.
  - `Ctrl + U` không thách gì đặc biệt ngoài những đường link không liên quan.
  - Bước thứ 2 là xem cookie, mình dùng [Cookie manager+](https://addons.mozilla.org/en-gb/firefox/addon/cookies-manager-plus/) trên firefox. Được cái đoạn này: `KimJongUn=TooLateNukesGone` nhưng `Fri 03 Mar 2017 04:28:51 PM UTC` ==> Hết hạn rồi. Điều tiếp theo mình nghĩ tới là làm thế nào để thay đổi thời gian làm cho cookie này có hiệu thực đây? ... Không thể nào! hoặc có thể là mình không biết. :(
  - Không biết làm sao hết. Tiến hành bước tiếp theo vậy, xem http header.
  - Bây giờ mới bắt đầu dùng tới `burpsuite`. Nhận được header response thế này:

```
HTTP/1.1 200 OK
Date: Fri, 03 Mar 2017 09:28:39 GMT
Server: Apache/2.4.7 (Ubuntu)
X-Powered-By: PHP/5.5.9-1ubuntu4.20
Set-Cookie: KimJongUn=2541d938b0a58946090d7abdde0d3890_b8e2e0e422cae4838fb788c891afb44f; expires=Fri, 03-Mar-2017 09:28:49 GMT; Max-Age=10
Set-Cookie: KimJongUn=TooLateNukesGone; expires=Fri, 03-Mar-2017 09:28:50 GMT; Max-Age=10
Vary: Accept-Encoding
Content-Length: 1117
Connection: close
Content-Type: text/html
```

  - Có thêm 1 cookie nữa, cookie mã hóa 2 đoạn md5 (mình đoán thế). Mình decrypt md5 trên <md5online.org> ra thế này: `send_nukes`. Âu cơ! submit thôi, nhớ thêm format flag `pragyanctf{send_nukes}`