# connect mongodb vs nodejs


- MongooseJS là một thư việc rất phổ biến trong Node.js, thư viện này cung cấp một sự rành mạch, giải pháp schema-based để đối tượng hóa dữ liệu ứng dụng của bạn và bao gồm built-in type casting, validation, query, building, business logic và nhiều thứ khác. Việc sử dụng mongoose bạn có thể làm việc với mongodb giống như một chuyên gia. Mongoose đơn giản để làm việc với mongodb và tăng độ tin cậy với những tính năng tự đông kết nối và quản lý connection pool. Để làm việc với mongoose chúng ta cần cài đặt module mongoose, dùng lệnh : 

```js
const mongoose = require('mongoose');
//khai báo mongoose
const connectDB = async () =>{
    try{
      const conn = await mongoose.connect(process.env.DB,{
        // process.env lấy một biến từ bên ngoài môi trường tránh bị người khác hoặc hacker có thể xem được database
        useUnifiedTopology : true,
        useNewUrlParser : true,
        useCreateIndex : true
        // các option bạn cần thêm 
      });
    console.log("Connect DB success !!")
    }catch(error){
       console.log(error);
       process.exit(1)
    }
}
module.exports = { connectDB }
```
- ở đoạn code trên sử dụng async await vì đây là một hàm bất đồng bộ khi kết nối database hoặc gọi api thì chúng ta nên sử dụng async await bởi vì cú pháp ngắn gọn và dễ hiểu.