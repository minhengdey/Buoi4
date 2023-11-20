## I. Tính đóng gói trong Java

**_Đóng gói (encapsulation) trong java_** là kỹ thuật ẩn giấu thông tin không liên quan và hiện thị ra thông liên quan. Mục đích chính của đóng gói trong java là giảm thiểu mức độ phức tạp phát triển phần mềm.

Đóng gói cũng được sử dụng để bảo vệ trạng thái bên trong của một đối tượng. Bởi việc ẩn giấu các biến biểu diễn trạng thái của đối tượng. Việc chỉnh sửa đối tượng được thực hiện, xác nhận thông qua các phương thức. Hơn nữa, việc ẩn giấu các biến thì các lớp sẽ không chia sẻ thông tin với nhau được. Điều này làm cho chương trình dễ quản lý hơn và có thể kiểm soát dữ liệu tốt hơn.

Để đạt được đóng gói trong Java ta cần:
- Khai báo các biến của một lớp là private.
- Cung cấp phương thức setter và getter là public để có thể sửa đổi và xem các giá trị biến.

_Ví dụ:_

- file SinhVien.java

```java
public class SinhVien {
    private String ten;
    public void setTen(String ten) {

        this.ten = ten;
    }
    public String getTen() {

        return ten;
    }
}
```

- file Main.java

```java
public class Main {
    public static void main(String[] args) {
        SinhVien sinhVien = new SinhVien();
        sinhVien.setTen("Minh Anh");
        System.out.println(sinhVien.getTen());
    }
}
//Output: Minh Anh
```

>- Vì biến `ten` được khai báo private nên để đề cập được đến biến này ở ngoài class `SinhVien`, ta cần dùng đến các phương thức public `getTen()` và `setTen()`:

  - `getTen()`: Lấy thông tin.
  - `setTen()`: Thay đổi thông tin.
  
## II. Tính kế thừa trong Java

**_Kế thừa (inheritance) trong java_** là sự liên quan giữa hai class với nhau, trong đó có class cha (superclass) và class con (subclass). Khi kế thừa class con được hưởng tất cả các phương thức và thuộc tính của class cha. Tuy nhiên, nó chỉ được truy cập các thành viên public và protected của class cha. Nó không được phép truy cập đến thành viên private của class cha.

Kế thừa giúp tái sử dụng mã nguồn, giảm độ lặp lại, thuận tiện trong việc bảo trì và nâng cấp chương trình.

Cú pháp:

```java
class Subclass extends Superclass {
// Code của lớp con
}
```

### Các loại kế thừa trong Java

#### a, Đơn kế thừa

**_Đơn kế thừa_** là khi một class kế thừa một class khác.

_Ví dụ:_

- file ConNguoi.java

```java
public class ConNguoi {
    public void ngu() {
        System.out.println("Khò khò");
    }
}
```

- file SinhVien.java

```java
public class SinhVien extends ConNguoi {
    public void hoc() {
        System.out.println("Tạch tạch");
    }
}
```

- file Main.java

```java
public class Main {
    public static void main(String[] args) {
        SinhVien sinhVien = new SinhVien();
        sinhVien.hoc();
        sinhVien.ngu(); // Kế thừa từ class ConNguoi
    }
}
/*Output:
Tạch tạch
Khò khò
*/
```

#### b, Kế thừa nhiều cấp

**_Kế thừa nhiều cấp_** là khi có một chuỗi kế thừa.

_Ví dụ:_

- file DongVat.java

```java
public class DongVat {
    public void tho() {
        System.out.println("Phì phì");
    }
}
```

- file ConNguoi.java

```java
public class ConNguoi extends DongVat {
    public void ngu() {
        System.out.println("Khò khò");
    }
}
```

- file SinhVien.java

```java
public class SinhVien extends ConNguoi {
    public void hoc() {
        System.out.println("Tạch tạch");
    }
}
```

- file Main.java

```java
public class Main {
    public static void main(String[] args) {
        SinhVien sinhVien = new SinhVien();
        sinhVien.hoc();
        sinhVien.ngu();
        /*
        Class SinhVien kế thừa từ class ConNguoi
         */
        sinhVien.tho();
        /*
        Class ConNguoi kế thừa từ class DongVat
        Class SinhVien kế thừa từ class ConNguoi
         */
    }
}
/*Output:
Tạch tạch
Khò khò
Phì phì
*/
```

#### c, Kế thừa thứ bậc

**_Kế thừa thứ bậc_** là khi có từ hai class trở lên kế thừa một class.

_Ví dụ:_

- file DongVat.java

```java
public class DongVat {
    public void tho() {
        System.out.println("Phì phì");
    }
}
```

- file ConNguoi.java

```java
public class ConNguoi extends DongVat {
    public void ngu() {
        System.out.println("Khò khò");
    }
}
```

- file ConMeo.java

```java
public class ConMeo extends DongVat {
    public void keu() {
        System.out.println("Meo meo");
    }
}
```

- file Main.java

```java
public class Main {
    public static void main(String[] args) {
        ConNguoi conNguoi = new ConNguoi();
        System.out.println("Con người:");
        conNguoi.ngu();
        conNguoi.tho(); // Kế thừa từ class DongVat
        System.out.println("Con mèo:");
        ConMeo conMeo = new ConMeo();
        conMeo.keu();
        conMeo.tho(); // Kế thừa từ class DongVat
    }
}
/*Output:
Con người:
Khò khò
Phì phì
Con mèo:
Meo meo
Phì phì
*/
```

## III. Tính đa hình trong Java

**_Đa hình (polymorphism) trong java_** là một khái niệm mà chúng ta có thể thực hiện một hành động bằng nhiều cách khác nhau.

Có hai kiểu của đa hình trong java, đó là đa hình lúc biên dịch (compile) và đa hình lúc thực thi (runtime). Chúng ta có thể thực hiện đa hình trong java bằng cách nạp chồng phương thức và ghi đè phương thức.

### Đa hình lúc thực thi (runtime)

**_Ghi đè (Overriding):_** là hai phương thức cùng tên, cùng tham số, cùng kiểu trả về nhưng thằng con viết lại và dùng theo cách của nó, và xuất hiện ở lớp cha và tiếp tục xuất hiện ở lớp con. Khi dùng override, lúc thực thi, nếu lớp Con không có phương thức riêng, phương thức của lớp Cha sẽ được gọi, ngược lại nếu có, phương thức của lớp Con được gọi.

>Lưu ý là quá trình quá trình ghi đè lúc runtime (hay overriding) chỉ xảy ra với các phương thức giống nhau về tham số và kiểu trả về. Các thuộc tính của đối tượng cha không thể bị ghi đè.

_Ví dụ:_

- file DongVat.java

```java
public class DongVat {
    public void tho() {
        System.out.println("Phì phì");
    }
}
```

- file ConMeo.java

```java
public class ConMeo extends DongVat {
    public void tho() {
        System.out.println("Khịt khịt");
    }
}
```

- file Main.java

```java
public class Main {
    public static void main(String[] args) {
        ConMeo conMeo = new ConMeo();
        conMeo.tho(); // Output: Khịt khịt
        DongVat dongVat = new DongVat();
        dongVat.tho(); // Output: Phì phì
    }
}
```

### Đa hình lúc biên dịch (compile)

**_Nạp chồng (Overloading):_** Đây là khả năng cho phép một lớp có nhiều thuộc tính, phương thức cùng tên nhưng với các tham số khác nhau về loại cũng như về số lượng. Khi được gọi, dựa vào tham số truyền vào, phương thức tương ứng sẽ được thực hiện.

Có 2 cách nạp chồng phương thức trong java

- Thay đổi số lượng các tham số
- Thay đổi kiểu dữ liệu của các tham số

_Ví dụ:_

- file Cong.java

```java
public class Cong {
    public int cong(int a, int b) {
        return a + b;
    }
    public double cong(double a, double b) {
        return a + b;
    }
    public int cong(int a, int b, int c) {
        return a + b + c;
    }
}
```

- file Main.java

```java
public class Main {
    public static void main(String[] args) {
        Cong cong = new Cong();
        System.out.println(cong.cong(2, 7));
        System.out.println(cong.cong(2.2, 3.3));
        System.out.println(cong.cong(2, 7, 4));
    }
}
/* Output:
9
5.5
13
 */
```