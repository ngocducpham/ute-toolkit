# UTE Toolkit
> Script nhỏ hỗ trợ đăng kí môn học nhanh **hơn chút xíu**

## Chuẩn bị
> Ở đây mình hướng dẫn cho trình duyệt Edge. Tuy vậy nhưng các bước cũng rất giống trên các trình duyệt khác

### Tạo Bookmark

Vào bất cứ trang web nào sau đó nhìn lên góc cuối phía bên phải của thanh địa chỉ sẽ thấy hình ngôi sao. Click vào và nhấn `Done`
   
### Chỉnh sửa Bookmark

> Lưu ý: Nếu không thấy dưới thanh địa chỉ có gì mới xuất hiện thì vào `Setting` tìm chỗ `Show favories bar` và chọn `Always`

Sau khi tạo xong bookmark sẽ thấy bên dưới thanh địa chỉ xuất hiện tên và biểu tượng của trang vừa thêm. 
   
Chuột phải vào nó và chọn `Edit`. Lúc này sẽ xuất hiện 1 hộp thoại.

   * Mục `Name` ghi tùy ý

   * Mục `URL` xóa tất cả và pass một trong những đoạn code dưới đây vào và nhấn `Done`

**Code đăng kí học phần**
```javascript
javascript: (() => {async function a(a) {let b = {method: "POST",credentials: "same-origin",headers: {"Content-Type": "application/x-www-form-urlencoded"},redirect: "error",body: new URLSearchParams({CurriculumID: a.curriculumID,StudyUnitID: a.studyUnitID,hdID: a.hdID,[a.name]: "on"})},c = await fetch("/DangKiNgoaiKeHoach/DanhSachLopHocPhanPost?Length=18", b);return c.text()}async function b(a) {let b = "/DangKiNgoaiKeHoach/DanhSachLopHocPhan/" + a + "?CurriculumID=" + a.slice(3) + "&t=" + Math.random(),c = await fetch(b, {method: "GET",credentials: "same-origin",redirect: "error"});return c.text()}async function c(a, c) {return await new Promise((e, f) => {if (!localStorage.getItem(c)) {b(a).then(a => {e(d(a, c))}).catch(() => {f()})} else {let courseInfo = JSON.parse(localStorage.getItem(c));e(Object.assign({}, courseInfo));}})}function d(a, b) {let c, d, e = new DOMParser().parseFromString(a, "text/html"),f = e.querySelector("#StudyUnitID").value,g = e.querySelector("#CurriculumID").value,h = !1,i = [],j = e.querySelectorAll(".trhover");for (row of j) {if (h) break;if (!row.querySelector(".classCheckChon").disabled) {let a = row.querySelectorAll("td");if (a[2].innerText == b) {c = row.querySelector(".classCheckChon").id + "|", d = row.querySelector(".classCheckChon").name, h = !0;break}i.push(a[2].innerText)}}let courseInfo = {found: h,studyUnitID: f,curriculumID: g,hdID: c,name: d,availableCourseCodes: i};localStorage.setItem(b, JSON.stringify(courseInfo));return courseInfo;}function e() {let a = new Date,b = a.getUTCFullYear() % 100,c = a.getUTCMonth();return 10 < c || 3 > c ? --b + "2" : b + "1"}if (!location.href.includes("dkmh.hcmute.edu.vn")) return void alert("Bạn hãy đăng nhập vào trang dkmh.hcmute.edu.vn trước khi chạy script này");if (null == document.querySelector("#id_menu2")) return void alert("Hãy đăng nhập trước khi chạy script");let f = prompt("Nhập mã lớp học phần (MaMonHoc_MaLop). Nếu nhập nhiều môn thì phân cách nhau bằng khoảng trắng. Ví dụ: ADNT330580_01CLC ADPL331379_03CLC");if (null != f && "" != f) {f = f.replace(/\s+/g, " ").trim().split(" ");for (const b of f) {let d = e() + b.split("_")[0];c(d, b).then(c => {c.found ? a(c).then(a => {let c = new DOMParser().parseFromString(a, "text/html");alert(c.querySelector("p").innerText + "Mã lớp học phần:  " + b)}).catch(() => {alert("Đăng kí không thành công, vui lòng đăng nhập lại.\nMã lớp học phần: " + b)}) : prompt("Không tìm thấy học phần phù hợp cho mã môn học. Có thể do mã lớp học phần không tồn tại hoặc lớp đã đầy." + b + "\nDanh sách học phần có sẵn: ", c.availableCourseCodes)}).catch(() => {alert("Đăng kí không thành công, vui lòng đăng nhập lại.\nMã lớp học phần: " + b)})}}})();
```

**Code xóa học phần**
```javascript
javascript: (() => {if (!window.location.href.includes("dkmh.hcmute.edu.vn")) return void alert("Bạn hãy đăng nhập vào trang dkmh.hcmute.edu.vn trước khi chạy script này");if (null == document.querySelector("#id_menu2")) return void alert("Hãy đăng nhập trước khi chạy script");let n = prompt("Nhập kì học.\nVí dụ: năm học 2021-2022, kì 2 thì nhập 212");if (null == n || "" == n) return;let h = prompt("Nhập mã môn học. Nếu nhập nhiều môn thì phân cách nhau bằng khoảng trắng. Ví dụ: ADNT330580 ADPL331379");if (null == h || "" == h) return;h = h.replace(/\s+/g, " ").trim().split(" ");for (let e = 0; e < h.length; e++) XoaHocPhan(h[e])})();
```

**Code lấy danh sách học phần đã đăng kí**
```javascript
javascript: (() => {fn().then(e=>{let t=(new DOMParser).parseFromString(e,"text/html"),n=t.querySelectorAll("table");n[0].style.setProperty("background-color","white"),n[1].style.setProperty("background-color","white"),document.body.insertAdjacentElement("afterbegin",n[1]),document.body.insertAdjacentElement("afterbegin",n[0]),scroll({top:0,behavior:"smooth"})}).catch(e=>{alert("Không lấy được danh sách môn học đã đăng kí , vui lòng đăng nhập lại.")}),alert("Nhấn OK sau đó đợi một lúc sẽ có kết quả");async function fn(){let e=await fetch("/dangkithanhcong",{method:"GET",credentials:"same-origin",redirect:"error"});return e.text()}})();
```

## Sử dụng

Sau khi hoàn thành các bước trên thì bạn chỉ cần vào `Đăng nhập` vào trang [Đăng Kí Môn Học](https://dkmh.hcmute.edu.vn/) và click vào bookmark bạn vừa thêm sẽ xuất hiện 1 hộp thoại, sau đó nhập thông tin theo hướng dẫn

**Chúc các bạn đăng kí môn học thành công 👍**

## FAQ
<details>
   <summary><b>Tại sao script lại luôn báo đăng kí không thành công?</b> (click to show)</summary>
   
Đây không phải công cụ thần thánh gì, nó chỉ giúp bạn bỏ qua một số bước để giúp cho việc đăng kí trở nên nhanh hơn, phần lớn đều phải phụ thuộc vào trang web trường và tốc độ mạng của bạn.
   
</details>

<details>
   <summary><b>Xài có mất nick facebook, google, v.v.. không??</b> (click to show)</summary>
   
Đương nhiên là không. Do script được viết bằng javascript, mà javascript thì trang nào cũng có. Nếu mà dễ mất nick vậy thì các bạn vào xem phim sẽ gầy chắc có khi mất cả trăm nick rồi.
   
</details>

<details>
   <summary><b>Xài có bị thầy cô phát hiện hay bị khóa đăng kí môn không? </b> (click to show)</summary>
   
Cái này mình không chắc nhưng có thể bị, nếu các bạn spam đăng kí quá nhiều trong một lần đăng nhập thì có thể bị block. Mà chỉ có thể nếu nhà trường có triển khai chức năng phát hiện :))
   
</details>

