
## dasar teori
Fungsi merupakan satu kesatuan rangkaian instruksi yang memberikan atau menghasilkan suatu nilai dan biasanya memetakkan input ke suatu nilai yang lain. Oleh karena itu, fungsi selalu menghasilkan/mengembalikan nilai. Suatu subprogram dikatakan fungsi apabila: 1. Ada deklarasi tipe nilai yang dikembalikan 2. Terdapat kata kunci return dalam badan subprogram. Maka fungsi digunakan jika suatu nilai biasanya diperlukan, seperti: - Assignment nilai ke suatu variabel - Bagian dari ekspresi - Bagian dari argumen suatu subprogram Karena itu selalu pilih nama fungsi yang menggambarkan nilai, seperti kata benda dan kata sifat. Contoh nama-nama fungsi: median, rerata, nilaiTerbesar, ketemu, selesai.

## Soal1

```go
  

package main

  

import "fmt"

  
  

func faktorial(n int) int {

    if n <= 1 {

        return 1

    }

    return n * faktorial(n-1)

}

  
  

func permutasi(n, r int) int {

    return faktorial(n) / faktorial(n-r)

}

  
  

func kombinasi(n, r int) int {

    return faktorial(n) / (faktorial(r) * faktorial(n-r))

}

  

func main() {

    var a, b, c, d int

    fmt.Print("Masukkan nilai a, b, c, d: ")

    fmt.Scan(&a, &b, &c, &d)

  

    if a >= c && b >= d {

        fmt.Printf("Permutasi(%d, %d) = %d, Kombinasi(%d, %d) = %d\n", a, c, permutasi(a, c), a, c, kombinasi(a, c))

        fmt.Printf("Permutasi(%d, %d) = %d, Kombinasi(%d, %d) = %d\n", b, d, permutasi(b, d), b, d, kombinasi(b, d))

    } else {

        fmt.Println("Input tidak memenuhi syarat (a >= c dan b >= d)")

    }

}
```

## output
![[Soal1.png]]


## Soal2
``` go
package main

  

import "fmt"

  

func main() {

    var a, b, c int

    fmt.Print("Masukkan nilai a, b, c: ")

    fmt.Scan(&a, &b, &c)

  

    hasil1 := (a + 1 - 2) * (a + 1 - 2)

    hasil2 := (b*b + 1) - 2

    hasil3 := (c-2)*(c-2) + 1

    fmt.Println("(f ∘ g ∘ h)(", a, ") =", hasil1)

    fmt.Println("(g ∘ h ∘ f)(", b, ") =", hasil2)

    fmt.Println("(h ∘ f ∘ g)(", c, ") =", hasil3)

}
```

## Output
![[Soal2.png]]

## Soal3
``` go
package main

import "fmt"

  

func dalamLingkaran(cx, cy, r, x, y int) bool {

    dx := x - cx

    dy := y - cy

    return dx*dx+dy*dy <= r*r

}

  

func main() {

    var x1, y1, r1 int

    var x2, y2, r2 int

    var x, y int

    fmt.Print("Masukkan pusat dan radius lingkaran 1 (x y r): ")

    fmt.Scan(&x1, &y1, &r1)

  

    fmt.Print("Masukkan pusat dan radius lingkaran 2 (x y r): ")

    fmt.Scan(&x2, &y2, &r2)

    fmt.Print("Masukkan titik sembarang (x y): ")

    fmt.Scan(&x, &y)

  

    diDalam1 := dalamLingkaran(x1, y1, r1, x, y)

    diDalam2 := dalamLingkaran(x2, y2, r2, x, y)

  

    if diDalam1 && diDalam2 {

        fmt.Println("Titik di dalam lingkaran 1 dan 2")

    } else if diDalam1 {

        fmt.Println("Titik di dalam lingkaran 1")

    } else if diDalam2 {

        fmt.Println("Titik di dalam lingkaran 2")

    } else {

        fmt.Println("Titik di luar lingkaran 1 dan 2")

    }

}
```

## Output
![[Soal3.png]]