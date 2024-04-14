# Module 1:
## Nội dung :
- Giới thiệu chương trình khóa học
- Kiểm tra cài đặt công cụ phần mềm
- Kết nối phần mềm, phần cứng
- Chạy chương trình đầu tiên

## Mục tiêu :
- Kiểm tra xem đã cài đặt phần mềm chưa
- Kết nối phần mềm, phần cứng và chạy chương trình đầu tiên
- Đảm bảo có board, board đó đã kết nối với phần mềm rồi, nạp được code rồi


# Module 2:
## Nội dung :
- GPIO - OUTPUT
- Các chân vi điều khiển, các chân IO
- Cấu trúc chân OUTPUT
- Giá trị Logic 0, Logic 1 của chân OUTPUT
- Lập trình điều khiển LED
- Debug

## Mục tiêu :
Với 1 chức năng mà mọi người có thể điều khiển tạo ra 1 cái mức điện áp/ mức logic trên 1 cái chân vi điều khiển
có điện áp 3.5V hoặc 0v bzw. mức logic 1 hoặc 0. Hiểu được các chân vi điều khiển, cấu trúc chân OUTPUT. Như thế nào
được hiểu là logic 1/0? Lập trình điều khiển LED và Debug đến cấp độ thanh ghi 


# Module 3:
## Nội dung :
- GPIO - INPUT
- Giá trị Logic 0, 1 của INPUT
- Các chế độ INPUT: Floating/PullUP/PullDown
- Lập trình đọc giá trị logic chân nối với nút nhấn
- Debug

## Mục tiêu :
- Dùng vi điều khiển để đạt được là hiện tại trên cái chân vi điều khiển đó đang có giá trị điện áp tương ứng với logic 1 hay 0. 
Tức là cái chân vi điều khiển đó sẽ được nối với 1 cái mạch bên ngoài. Mạch này hoạt động tạo ra 1 giá trị diện áp 
đặt lên chân vi điều khiển. Ta sủ dụng mã code để đọc ra hiện tại tren cái chân đó là logic 1 hay logic 0. Định nghĩa logic 0,1 của INPUT có
thể khác so với OUTPUT để đảm bảo tính tương thích. CẦN PHẢI NẮM RÕ CÁI NÀY ĐỂ CÓ THỂ GHÉP NỐI VS NHAU PHÙ HỢP.
- Hiểu được cái chế độ INPUT. Ta thấy: LED là 1 thiết bị hiển thị (indicator), ta bt đc giá trị logic trên chân là bao nhiêu. Còn với nút nhấn
thì là 1 thiết bị INPUT, ta nhấn nút sẽ kích mạch đó hoạt động và sẽ điều khiển giá trị


# Module 4:
## Nội dung :
- GPIO-INPUT, OUTPUT
- Giao tiếp điều khiển LED 7 đoạn
- Kết nối INPUT, OUTPUT
- Debug

## Mục tiêu :
Điều khiển LED 7 đoạn thông qua 1 IC dịch (IC shift), dùng để dịch dữ liệu để chuyển tiếp dữ liệu nối tiếp sang dữ liệu song song.
Ta phải viết code C, hiểu về ngoại vi


# Module 5:
## Nội dung :
- EXIT ngắt ngoài
- Tổng quan về ngắt , nguyên lý hoạt động
- Độ ưu tiên ngắt
- Debug

## Mục tiêu :
vi xử lý được thiết kế vs 1 khái niệm được gọi là ngoại lệ. Đây là 1 sự kiện nào đó làm thay đổi thứ tự 
thực hiện của chương trình. Trong chương trình C thông thường thì sẽ thực hiện lệnh từ trên xuống dưới. 
1 chương trình C bình thường thì có thể tiên đoán được câu lệnh tiếp theo được thực hiện là gì. Về ngắt thì không
như vậy. Ngắt thì bất cứ lúc nào vi xử lý cũng có thể bị interrupted, bị chiếm dụng bởi 1 luồng chương trình khác.
Tức là vi xử lý đang làm việc bình thường như vậy nhưng mà phải tạm ngưng lại để xử lý rồi mới quay lại. Việc 
tạm ngưng lại này có thể diễn ra bất cứ lúc nào. Do đó vi xử lý có được sự linh hoạt, đáp ứng được các sự kiện cần được đpá ứng ngay.
EXTI: các sự kiện, tín hiệu ngắt đến từ chân vi điều khiển


# Module 6:
## Nội dung : 
- Clock
- Nguồn Clock
- Sơ đồ phân phối clock
- System Tick Timer và hàm HAL_delay(ms)

## Mục tiêu :
Clock là nguồn dao động 101010. 1 số vi điều khiển ta có thể không cần quan tâm đến clock thì nó vẫn chạy
Ví dụ như làm Arduino không cần quan tâm Clock. Tuy nhiên khi đặt vào 1 bài toán cụ thể phải tối ưu tính toán về mặt thời gian
thì phải nắm rõ về clock. 


## Module 7:
## Nội dung :
- Tổng quan về truyền nhận dữ liệu
- UART - TX
- Nguyên lý hoạt động
- Truyền các kiểu dữ liệu khác nhau
- Debug

## Mục tiêu :
Hiểu về 1 chuẩn giao tiếp truyền nhận dũ liệu UART( Universal asynchronous receiver transmitter). Ta sẽ hiểu thế nào là chuyền dữ liệu song song, nối tiếp, 
full duplex, half duplex. Hiểu được giao tiếp UART đén từng Bit: Nó được truyền ntn? Nó được đóng gói vào 1 package ntn, nó đồng bộ với nhau ntn? Ta sẽ được hướng dẫn
để có thể truyền các kiểu dữ liệu khavs nhau (kí tự, chuỗi, số thực, số nguyên, ...)


## Module 8:
## Nội dung :
- UART - RX
- Nguyên lý hoạt động
- Nhận ký tự, chuỗi dữ liệu sử dụng ngắt
- Xử lý chuỗi với thư viện string.h
- Debug

## Mục tiêu :
Nhận dữ liệu sẽ khó hơn truyền. Truyền thì lúc nào ta muốn truyền thì ta gọi lệnh để truyền. Nhưng nhận là vi điều khiển đang ở thế bị động, 
ta phải thiết kế để bất cứ khi nào tín hiệu được truyền tới thì vi xử lý phải nhận đc dữ liệu tránh mất mát. Ta phải đảm bảo nhận được đúng thời điểm,
đủ dữ liệu, bóc tách các thông tin từ gói dữ liệu nhận được.


# Module 9:
## Nội dung :
- TIMER - Timebase
- Cấu trúc, nguyên lý hoạt động Timebase
- Ngắt Timebase
- Debug

## Mục tiêu :
Hiểu được chức năng, nguyên lý Timebase (kiến thức nền tảng) đén từng thanh ghi. Với chức năng timebase ta cũng sẽ sử dụng
ngắt bởi vì nó liên quan đến yếu tố thời gian, độ chính xác về thời gian thì phải dùng ngắt. Không có ngắt sẽ bị trễ, không 
chính xác


# Module 10:
## Nội dung :
- TIMER - PWM
- Cấu trúc, nguyên lý hoạt động PWM
- Điều khiển độ sáng LED
- Debug

## Mục tiêu :
Điều chế độ rộng xung PWM, được ứng dụng trong tạo ra mức điện áp trung bình, VD: làm mạch ổn áp, điều khiển động cơ, độ sáng dimmer.


# Module 11:
## Nội dung :
- ADC- Polling
- Nguyên lý hoạt động
- Chuyển đổi ADC 1 kênh ngõ vào
- Thực hành với biến trở
- Debug

## Mục tiêu :
Ngoại vi ADC, cơ chế Polling. Nguyên lý hoạt động của ADC ntn? bộ ADC XAR hoạt động ntn? Làm sao từ 1 điện áp
không biết là bao nhiêu mà nó chuyển đổi ra đc 1 giá trị số mà từ đó ta tính toán đc điện áp là bnh. Thực hành vs thiết bị 
điều chỉnh được điện áp đó là biến trở.


# Module 12:
## Nội dung :
- ADC -IT
- Thực hành kết hợp ADC - TIMER
- Thuật toán trung bình động (moving average) với mảng dữ liệu
- Debug

## Mục tiêu :
Tìm hiểu ADC với chế độ ngắt. Thực hành kết hợp ngoại vi ADC và TIMER
