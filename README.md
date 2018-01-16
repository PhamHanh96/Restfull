# Restfull

﻿# refull_3H
This is the report  our group

# Mô hình Client và Server của RESTful Web Service
## I) REST là gì?
- Web Service là 1 dịch vụ web, cung cấp các thông tin thô và khó hiểu so với đa số người dùng, chính vì vậy nó được sử dụng bởi các ứng dụng. Các ứng dụng này sẽ chế biến các dữ liệu thô trước khi trả về cho người dùng cuối cùng.
 ![4310909](https://user-images.githubusercontent.com/35052781/34906912-0e85f158-f8a9-11e7-8504-a6d94384e0aa.png)
- Các Web Service thường cung cấp các dữ liệu thô nên chúng thường được trả về dưới dạng XML hoặc JSON.
- Ví dụ: Bạn vào một trang web nào đó để xem thông tin về thời tiết, để có được các dữ liệu bạn muốn thì trang web đó cần phải lấy thông tin từ 1 nguồn nào đó, các dữ liệu sẽ được chế biến trước khi trả về cho bạn là một trang web hoàn chỉnh.

 ![4311054](https://user-images.githubusercontent.com/35052781/34906988-1a0c54f8-f8aa-11e7-8038-cdd54ff9d1a2.png)
- RESTful Web Service là các Web Service được viết dựa trên cấu trúc REST, được sử dụng rộng rãi thay thế cho các Web Service dựa trên SOAP và WSDL.
- Trong kiến trúc REST mọi thứ đều được coi là tài nguyên, chúng có thể là: tệp văn bản, ảnh, trang html, video, hoặc dữ liệu động… REST server cung cấp quyền truy cập vào các tài nguyên, REST client truy cập và thay đổi các tài nguyên đó. Ở đây các tài nguyên được định danh dựa vào URI, REST sử dụng một vài đại diện để biểu diễn các tài nguyên như văn bản, JSON, XML.

## II) RESTful web service
 Có bốn quy tắc cơ bản để cài đặt một RESTful web service:
### 1. Sử dụng các phương thức HTTP một cách rõ ràng.
-  REST đòi hỏi lập trình viên xác định rõ ý định của mình thông qua các phương thức của HTTP, bao gồm lấy dữ liệu, chèn dữ liệu, cập nhật dữ liệu hoặc xóa dữ liệu. Các quy tắc:
   + Để tạo một tài nguyên trên máy chủ, bạn cần sử dụng phương thức POST.
   +  Để truy xuất một tài nguyên, sử dụng GET.
   +  Để thay đổi trạng thái một tài nguyên hoặc để cập nhật nó, sử dụng PUT.
   +  Để huỷ bỏ hoặc xoá một tài nguyên, sử dụng DELETE.
- Tuy nhiên, các nguyên tắc ở trên là không bắt buộc, thực tế ta có thể sử dụng phương thức GET để yêu cầu lấy dữ liệu, chèn, sửa hoặc xóa dữ liệu trên Server. REST đưa ra các nguyên tắc trên với mục đích đưa mọi thứ trở nên rõ ràng và dễ hiểu hơn.
### 2. Phi trạng thái
- Một đặc điểm của REST là phi trạng thái (stateless), có nghĩa là nó không lưu giữ thông tin của client.
- Ví dụ: Bạn vừa gửi yêu cầu để xem trang thứ 2 của một tài liệu, và bây giờ bạn muốn xem trang thứ 3(trang tiếp theo). REST sẽ không lưu trữ lại thông tin rằng trước đó bạn đã xem trang số 2. Điều đó có nghĩa là REST không quản lý phiên làm việc(Session).
- Hình minh họa một ứng dụng có lưu trữ trạng thái, nó biết người dùng đang xem trang số mấy và người dùng chỉ cần yêu cầu trang tiếp theo để nhận được trang mong muốn.
 ![4311836](https://user-images.githubusercontent.com/35052781/34907318-3d95d61a-f8af-11e7-9f46-ad13bc9e0841.png)
 
  Còn với các thiết kế phi trạng thái, Client phải gửi yêu cầu rõ ràng, bao gòn số thứ tự của trang cần xem.
 ![4311864](https://user-images.githubusercontent.com/35052781/34907331-81ec84ee-f8af-11e7-91d2-cd1f48fa5c1b.png)
- Các thành phần máy chủ phi trạng thái ít phức tạp hơn để thiết kế, viết và phân bổ thông qua máy chủ được cân bằng. Dịch vụ phi trạng thái không chỉ hoạt động tốt hơn, nó còn chuyển hầu hết vai trò duy trì trạng thái sang ứng dụng ở máy khách.
### 3. Đưa ra cấn trúc thư mục giống các URI
- REST đưa ra một cấu trúc để người dùng có thể truy cập vào tài nguyên của nó thông qua các URL, tài nguyên ở đây là tất cả những cái mà chúng ta có thể gọi tên được (Video, ảnh, báo cáo chứng khoán, giá vàng...)
- Bạn cần tạo ra các REST serivce để nó trả về cho người dùng các nguồn tài nguyên tương ứng. Các địa chỉ REST service cần phải thật trực quan đến mức người dùng dễ đoán rằng nó đang trỏ tới cái gì và cung cấp tài nguyên gì. Tóm lại, cấu trúc của một URI nên được đơn giản, có thể dự đoán, và dễ hiểu.
- Một vài nguyên tắc bổ sung để lưu ý trong khi nói về cấu trúc địa chỉ của RESTful Web service là:
  + Giấu các đuôi tài liệu mở rộng của bản gốc trong máy chủ (.jsp, .php, .asp), nếu có, vì vậy bạn có thể giấu một số thứ mà không cần thay đổi địa chỉ Urls.
  + Để mọi thứ là chữ thường.
  + Thay thế các khoảng trống bằng gạch chân hoặc hoặc gạch nối (một trong hai loại).
  + Tránh các chuỗi yêu cầu càng nhiều càng tốt.
  + Thay vì sử dụng mã (404 Not Found) khi yêu cầu địa chỉ cho một phần đường dẫn, luôn luôn cung cấp một trang mặc định hoặc tài nguyên như một phản hồi.
### 4. Truyền tải XML, JSON hoặc cả hai.
- Khi Client gửi một yêu cầu tới web service nó thường được truyền tải dưới dạng XML hoặc JSON và thông thường nhận về với hình thức tương tự.
- Đôi khi Client cũng có thể chỉ định kiểu dữ liệu nhận về mà nó mong muốn (JSON, hoặc XML,..), các chỉ định này được gọi là các kiểu MINE, nó được gửi kèm trên phần HEADER của request. 
- Dưới đây là các kiểu MINE phổ biến thường sử dụng với REST service.
  + JSON
  Ví dụ: {
           "gia": 1000000,

           "hinhanh": null,
        
           "masanpham": 1,

           "math": 5,

           "soluong": 1,

           "tensanpham": "galaxy s7",

           "tinhtrang": "rat moi"
	        }
    
  + XML
  Ví dụ: 
  
       ``` <root>```
          <ul>```<gia>1000000</gia>```</ul>
          <ul>```<hinhanh>null</hinhanh```></ul>
          <ul>```<masanpham>1</masanpham>```</ul>
          <ul>```<math>5</math>```</ul>
          <ul>```<soluong>1</soluong>```</ul>
          <ul>```<tensanpham>galaxy s7 </tensanpham>```</ul>
          <ul>```<tinhtrang>rat moi </tinhtrang>```</ul>
 	     ``` </root>```
       
  + XHTML
- Điều này cho phép các service sử dụng bởi các client viết bởi các ngôn ngữ khác nhau, chạy trên nhiều nền tảng và thiết bị khác nhau. Sử dụng các kiểu MIME cho phép client chọn dạng dữ liệu phù hợp với nó.

# Ưu điểm của RESTfull Web Service
- REST Không có tools đắt tiền nào yêu cầu tương tác với Web service
- REST Smaller learning curve
- REST hiệu quả (SOAP sử dụng XML cho tất cả các truyền tin, REST có thể sử dụng định dạng truyền tin ngắn gọn hơn)
- REST nhanh (không yêu cầu xử lý rộng rãi)
- REST gần gũi hơn với các công nghệ Web khác trong triết lý design.
- REST sử dụng chuẩn HTTP nên nó đơn giản hơn nhiều so với trước đây. Tạo clients, phát triển các API, tài liệu dễ hiểu hơn và không có nhiều thứ mà REST không làm được. Về cơ bản điều này thực sự tốt hơn SOAP
- REST cho phép nhiều định dạng dữ liệu khác nhau trong khi SOAP chỉ cho phép XML. Mặc dù điều này có vẻ như làm tăng thêm sự phức tạp cho REST vì bạn cần phải xử lý nhiều định dạng. Nhưng theo kinh nghiệm, nó lại thực sự có lợi. JSON phù hợp hơn cho dữ liệu và phân tích cú pháp nhanh hơn. REST cho phép hỗ trợ tốt hơn cho browser client do nó có hỗ trợ cho JSON.
- REST có hiệu suất tốt hơn và khả năng mở rộng. Những lần đọc của REST có thể cached lại được còn SOAP thì không.
- Có một điều thú vị là REST hoàn toàn có thể sử dụng SOAP web services để thực hiện.

# Các công nghệ , nền tảng cho Server side
  -	Server-side là tên gọi chung của các ngôn ngữ chạy trên Server.
  -	Sử dụng :
    -	Xử lý user input (dữ liệu người dung nhập vào).
    -	Hiển thị trang.
    -	Cấu trúc lại một ứng dụng web.
    -	Tương tác với các bộ lưu trữ vĩnh viễn (SQL, file).
  -	Các ngôn ngữ lập trình phía server :
    -	PHP
    -	Ruby
    -	Python
    -	Javascript
    -	Perl
    -	C#, C/C++, Java, VB.net ….
  -	Nền tảng phát triển ứng dụng :
    -	Nodejs : là nền tảng sử dụng ngôn ngữ Javascript để phát triển ứng dụng phía server side. 
    -	Gem : sử dụng  ngôn ngữ  Ruby.
    -	Cpan : sử dụng  ngôn ngữ Perl.
  -	Tuy nhiên :
    -	Các ngôn ngữ trong bộ .net (C #, VB.net, ASP.net,…): không dung để làm ứng dụng  web, chúng được dùng để viết trên dịch vụ web            tầng ứng dụng (application-level web service). Ví dụ: lập trình các ứng dụng chạy ngầm server, webservice, web application, lập            trình socket, giao thức , …
    -	Java: lập trình các ứng dụng Webservice, web application, cấu hình server, các ứng dụng chạy nền phía server, lập trình các giao           thức, …
    -	PHP : ngôn ngữ lập trình các ứng dụng web, webservice và web application…
    -	Ruby : ngôn ngữ lập trình webserive, web application…
    -	Python: ngôn ngữ lập tình webservice, web application, cấu hình server..
    -	C/C++ : Lập trình các giao thức server, các module tối ưu hệ thống , lập trình server…

# Các công nghệ để xây dựng một ứng dụng phía Client
 Có rất nhiều công nghệ được nhắc đến trong thời gian gần đây và được lựa chọn trong việc xây dựng và phát triển ứng dụng phía Client. Xây dựng trang web cơ bản phía Front-End chúng ta có:

 -   HTML
 -   CSS
 -   Javascript

Những thư viện, framework nổi tiếng để xây dựng một ứng dụng web hoàn chỉnh phía Client đó là:

 -    Vue.js
 -    Angular
 -    React

 Trong đó `Angular` được coi là một `framework` hoàn chỉnh để xây dựng ứng dụng Web, được Google đầu tư xây dựng và phát triển, cộng đồng hỗ trợ đông đảo, nhiều sản phẩm công nghệ lớn sử dụng, có thể dùng để phát triển ứng dụng di động. 

 Bên cạnh đó, xây dựng ứng dụng di động chúng ta có `Android` và `Swift` (lập trình ứng dụng iOS).

***Chú ý: *** HTML và CSS không phải là ngôn ngữ lập trình, nó chỉ giúp định dạng website để hiển thị khi Client nhận phản hồi từ Server và các ngôn ngữ này là `ngôn ngữ markup`.
