# UTE Toolkit
> Script nhỏ hỗ trợ đăng kí môn học nhanh **hơn chút xíu**


## Chuẩn bị
> Ở đây mình hướng dẫn cho trình duyệt Edge. Tuy vậy nhưng các bước cũng rất giống trên các trình duyệt khác

### Tạo Bookmark

Vào bất cứ trang web nào sau đó nhìn lên góc cuối phía bên phải của thanh địa chỉ sẽ thấy hình ngôi sao. Click vào và nhấn `Done`

Sau khi tạo xong bookmark sẽ thấy bên dưới thanh địa chỉ xuất hiện tên và biểu tượng của trang vừa thêm. 

> Lưu ý: Nếu không thấy dưới thanh địa chỉ có gì mới xuất hiện thì vào `Setting` tìm chỗ `Show favories bar` và chọn `Always`
   
### Chỉnh sửa Bookmark
   
Chuột phải vào bookmark và chọn `Edit`. Lúc này sẽ xuất hiện 1 hộp thoại.

   * Mục `Name` ghi tùy ý

   * Mục `URL` xóa tất cả và pass một trong những đoạn code dưới đây vào và nhấn `Done`

**Code đăng kí học phần**
```javascript
javascript: (() => {async function a(a) {let b = {method: "POST",credentials: "same-origin",headers: {"Content-Type": "application/x-www-form-urlencoded"},redirect: "error",body: new URLSearchParams({CurriculumID: a.curriculumID,StudyUnitID: a.studyUnitID,hdID: a.hdID,[a.name]: "on"})},c = await fetch("/DangKiNgoaiKeHoach/DanhSachLopHocPhanPost?Length=18", b);return c.text()}async function b(a) {let b = "/DangKiNgoaiKeHoach/DanhSachLopHocPhan/" + a + "?CurriculumID=" + a.slice(3) + "&t=" + Math.random(),c = await fetch(b, {method: "GET",credentials: "same-origin",redirect: "error"});return c.text()}async function c(a, c) {return await new Promise((e, f) => {if (!localStorage.getItem(c)) b(a).then(a => {e(d(a, c))}).catch(() => {f()});else {let a = JSON.parse(localStorage.getItem(c));e(Object.assign({}, a))}})}function d(a, b) {let c, d, e = new DOMParser().parseFromString(a, "text/html"),f = e.querySelector("#StudyUnitID").value,g = e.querySelector("#CurriculumID").value,h = !1,i = [],j = e.querySelectorAll(".trhover");for (row of j) {if (!0 === h) break;let a = row.querySelectorAll("td");if (a[2].innerText == b) {row.querySelector(".classCheckChon").disabled ? h = null : (c = row.querySelector(".classCheckChon").id + "|", d = row.querySelector(".classCheckChon").name, h = !0);break}i.push(a[2].innerText)}let k = {found: h,studyUnitID: f,curriculumID: g,hdID: c,name: d,availableCourseCodes: i};return localStorage.setItem(b, JSON.stringify(k)), k}function e() {let a = new Date,b = a.getUTCFullYear() % 100,c = a.getUTCMonth();return 2 > c ? --b + "2" : b + "1"}if (!location.href.includes("dkmh.hcmute.edu.vn")) return void alert("B\u1EA1n h\xE3y \u0111\u0103ng nh\u1EADp v\xE0o trang dkmh.hcmute.edu.vn tr\u01B0\u1EDBc khi ch\u1EA1y script n\xE0y");if (null == document.querySelector("#id_menu2")) return void alert("H\xE3y \u0111\u0103ng nh\u1EADp tr\u01B0\u1EDBc khi ch\u1EA1y script");let f = prompt("Nh\u1EADp m\xE3 l\u1EDBp h\u1ECDc ph\u1EA7n (MaMonHoc_MaLop). N\u1EBFu nh\u1EADp nhi\u1EC1u m\xF4n th\xEC ph\xE2n c\xE1ch nhau b\u1EB1ng kho\u1EA3ng tr\u1EAFng. V\xED d\u1EE5: ADNT330580_01CLC ADPL331379_03CLC");null == f || "" == f || (f = f.replace(/\s+/g, " ").trim().split(" "), setInterval(() => {for (const b of f) {let d = e() + b.split("_")[0];c(d, b).then(c => {!1 === c.found ? (prompt("Kh\xF4ng t\xECm th\u1EA5y h\u1ECDc ph\u1EA7n ph\xF9 h\u1EE3p cho m\xE3 m\xF4n h\u1ECDc " + b + "\nDanh s\xE1ch h\u1ECDc ph\u1EA7n c\xF3 s\u1EB5n: ", c.availableCourseCodes), f = f.filter(a => a != b)) : !0 === c.found && (f = f.filter(a => a != b), a(c).then(a => {let c = new DOMParser().parseFromString(a, "text/html"),d = c.querySelector("p").innerText;d && alert(d + "M\xE3 l\u1EDBp h\u1ECDc ph\u1EA7n: " + b)}).catch(() => {alert("\u0110\u0103ng k\xED kh\xF4ng th\xE0nh c\xF4ng, vui l\xF2ng \u0111\u0103ng nh\u1EADp l\u1EA1i.\nM\xE3 l\u1EDBp h\u1ECDc ph\u1EA7n: " + b)}))}).catch(() => {alert("\u0110\u0103ng k\xED kh\xF4ng th\xE0nh c\xF4ng, vui l\xF2ng \u0111\u0103ng nh\u1EADp l\u1EA1i.\nM\xE3 l\u1EDBp h\u1ECDc ph\u1EA7n: " + b)})}}, 5e3))})();
```

**Code xóa học phần**
```javascript
javascript: (() => {if (!window.location.href.includes("dkmh.hcmute.edu.vn")) return void alert("Bạn hãy đăng nhập vào trang dkmh.hcmute.edu.vn trước khi chạy script này");if (null == document.querySelector("#id_menu2")) return void alert("Hãy đăng nhập trước khi chạy script");let n = prompt("Nhập kì học.\nVí dụ: năm học 2021-2022, kì 2 thì nhập 212");if (null == n || "" == n) return;let h = prompt("Nhập mã môn học. Nếu nhập nhiều môn thì phân cách nhau bằng khoảng trắng. Ví dụ: ADNT330580 ADPL331379");if (null == h || "" == h) return;h = h.replace(/\s+/g, " ").trim().split(" ");for (let e = 0; e < h.length; e++) XoaHocPhan(h[e])})();
```

**Code lấy danh sách học phần đã đăng kí**
```javascript
javascript:(()=>{(async function(){let a=await fetch("/dangkithanhcong",{method:"GET",credentials:"same-origin",redirect:"error"});return a.text()})().then(a=>{let b=new DOMParser().parseFromString(a,"text/html"),c=b.querySelectorAll("table");c[0].style.setProperty("background-color","white"),c[1].style.setProperty("background-color","white"),document.body.insertAdjacentElement("afterbegin",c[1]),document.body.insertAdjacentElement("afterbegin",c[0]),scroll({top:0,behavior:"smooth"})}).catch(()=>{alert("Kh\xF4ng l\u1EA5y \u0111\u01B0\u1EE3c danh s\xE1ch m\xF4n h\u1ECDc \u0111\xE3 \u0111\u0103ng k\xED , vui l\xF2ng \u0111\u0103ng nh\u1EADp l\u1EA1i.")}),alert("Nh\u1EA5n OK sau \u0111\xF3 \u0111\u1EE3i m\u1ED9t l\xFAc s\u1EBD c\xF3 k\u1EBFt qu\u1EA3")})();
```

**Code lấy thời khóa biểu**
```javascript
javascript:(()=>{function a(){let a=new Date,b=a.getUTCFullYear(),c=a.getUTCMonth();return 2>c?{yearStudy:b-1+"-"+b,termID:"HK02",week:10}:{YearStudy:b+"-"+b+1,TermID:"HK01",Week:35}}(async function(){let b=a(),c=new URLSearchParams({YearStudy:b.yearStudy,TermID:b.termID,Week:b.week}),d="/ThoiKhoaBieu/HienthiTKB?"+c.toString(),e=await fetch(d,{redirect:"error",credentials:"same-origin"});return e.text()})().then(a=>{let b=new DOMParser().parseFromString(a,"text/html"),c=b.querySelector("div");c.style.backgroundColor="white",document.body.insertAdjacentElement("afterbegin",c),scroll({top:0,behavior:"smooth"})}).catch(()=>{alert("Kh\xF4ng l\u1EA5y \u0111\u01B0\u1EE3c th\u1EDDi kh\xF3a bi\u1EC3u, vui l\xF2ng \u0111\u0103ng nh\u1EADp l\u1EA1i.")})})();
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

