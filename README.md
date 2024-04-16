# Sorting-System-by-Colors
Dự án mô phỏng và lập trình hệ thống phân loại và đóng gói sản phẩm dựa theo màu sắc dùng PLC với Factory IO.

## Hệ thống phân loại theo màu sắc
Hệ thống phân loại sản phẩm theo màu sắc và đóng nắp gổm 3 bộ phận chính:
<ul>
  <li> Bộ phận thứ nhất: Khối xử lý nhận dạng và đưa ra quyết định, gồm hệ thống cảm biến màu sắc. Khi sản phẩm đi qua cảm biến màu, cảm biến sẽ nhận biết màu và đưa tín hiệu cho phần mềm phân loại, phần mềm này sẽ thực hiện nhận dạng và quyết định sản phẩm thuộc loại nào</li>
  <li>Bộ phận thứ hai: Khối xử lý tín hiệu hỏi và đáp, điều khiển và giao tiếp giữa người và máy, gồm các nút ấn, màn hình.</li>
  <li>Bộ phận thứ ba: Khối các cơ cấu cơ khí chấp hành, gồm hai hệ băng chuyền liên tiếp nhau, có các khe được đặt nối tiếp theo băng chuyền. Trên hệ băng chuyền đầu tiên có 3 vị trí phân loại sản phẩm, ứng với mối sản phẩm có màu sẽ được phân loại. Bộ xử lý sẽ nhận dạng và ra quyết định là sản phẩm thuộc màu nào, sản phẩm sẽ được đưa tới thùng chứa được định trước về màu sắc. Trên hệ băng chuyền thứ hai có các tay máy và thiết bị cố định vị trí giúp đóng nắp hộp vào hộp trước khi di chuyển ra khỏi hệ thống.</li>
</ul>

## Quy trình phân loại màu nắp của sản phẩm

![image](https://github.com/HaoNguyen0201/Sorting-System-by-Colors/assets/137909212/2d499f26-9269-41b3-9e34-dfefe2d691e4)
![image](https://github.com/HaoNguyen0201/Sorting-System-by-Colors/assets/137909212/a9282cf5-448b-4428-b8dd-5b987aa908b9)

Khối SR đảm nhận chính trong nhiệm vụ này với chức năng được mô tả như sau:

![image](https://github.com/HaoNguyen0201/Sorting-System-by-Colors/assets/137909212/f72e0e14-3e9a-4bb9-a493-9db814c3133a)

Khi cảm biến nhận biết được đúng màu sắc của nắp hộp nó sẽ tiến hành kích hoạt một Pusher để đẩy sản phẩm sang băng tải vận chuyển đến chu trình tiếp theo. Đồng thời cũng kiểm tra xem băng tải đã hết hành trình đẩy của mình chưa, khi pusher đã hết hành trình đẩy mới thu piston của pusher về.
Ngoài ra trạng thái hoạt động của hệ thống băng chuyền cũng có thể được điều khiển dựa vào trạng thái của các nút nhấn được thể hiện qua:

![image](https://github.com/HaoNguyen0201/Sorting-System-by-Colors/assets/137909212/6375730e-3127-48cf-a2d0-7193f66d6991)

## Hệ thống đóng nắp vào thân sản phẩm 

![image](https://github.com/HaoNguyen0201/Sorting-System-by-Colors/assets/137909212/d2b8aaed-f371-4c38-8b3d-3b09ba4da1f0)

Khối giúp kiểm tra các điều kiện vào như trạng thái nút nhất khẩn cấp, dừng, sản phẩm đang trong quá trình lắp, hay vị trí của thân và nắp, để khởi động hoặc dừng quá trình vận chuyển của các băng chuyền chứa thân và nắp:

![image](https://github.com/HaoNguyen0201/Sorting-System-by-Colors/assets/137909212/217bd665-a77a-4f82-a8fa-d89bc5a87ec0)

![image](https://github.com/HaoNguyen0201/Sorting-System-by-Colors/assets/137909212/3205c266-3cb4-46d1-bddf-40ec625554ad)

Khối giúp kiểm tra vị trí của nắp để tiến hành kẹp nắp lại và nhả nắp ra khi tay máy 2 trục đã gắp được nắp:

![image](https://github.com/HaoNguyen0201/Sorting-System-by-Colors/assets/137909212/a1eea6eb-95e8-4023-8b47-00e35ab5bac9)

Khối giúp bàn kẹp cố định vị trí của phần thân sản phẩm khi đúng vị trí và nhả ra sau reset:

![image](https://github.com/HaoNguyen0201/Sorting-System-by-Colors/assets/137909212/2dc8204a-b7c7-4af2-b564-647caf7e4e79)

Khối giúp tay máy 2 trục tiến hành di chuyển lên xuống theo phương thẳng đứng dựa vào các điều kiện của bàn kẹp, vị trí sản phẩm, các trạng thái của tay máy,..

![image](https://github.com/HaoNguyen0201/Sorting-System-by-Colors/assets/137909212/8fed7cea-58f6-47da-ba0b-63f360f618ab)

Khối giúp tay máy hai trục giúp tay máy di truyển qua lại theo phương ngang để chuyển vị trí của nắp sang băng tải chứa thân sản phẩm dựa vào sự tuần tự đối với hoạt động của tay máy theo trục thẳng đứng:

![image](https://github.com/HaoNguyen0201/Sorting-System-by-Colors/assets/137909212/387aefda-6a6a-480b-8d98-1608d2c3f596)

Khối giúp bàn kẹp nâng lên và hạ xuống để phần thân tiếp tục di chuyển vào đúng vị trí cho việc lắp ghép tiếp theo vị trí:

![image](https://github.com/HaoNguyen0201/Sorting-System-by-Colors/assets/137909212/b356ccad-7921-43e9-bbbc-a9bd9517ba91)



