
## Dasar teori
Prosedur dapat dianggap sebagai potongan beberapa instruksi program menjadi suatu instruksi baru yang dibuat untuk mengurangi kerumitan dari kode program yang kompleks pada suatu program yang besar. Prosedur akan menghasilkan suatu akibat atau efek langsung pada program ketika dipanggil pada program utama. Suatu subprogram dikatakan prosedur apabila: 1. Tidak ada deklarasi tipe nilai yang dikembalikan 2. Tidak terdapat kata kunci return dalam badan subprogram. Kedudukannya prosedur sama seperti instruksi dasar yang sudah ada sebelumnya (assignment) dan/atau instruksi yang berasal dari paket (fmt), seperti fmt.Scan dan fmt.Print. Karena itu selalu pilih nama prosedur yang berbentuk kata kerja atau sesuatu yang merepresentasikan proses sebagai nama dari prosedur.

## unguided
## soal1
``` go
package main

  

import "fmt"

  

func factorial(n int) int {

    if n == 0 {

        return 1

    }

    result := 1

    for i := 2; i <= n; i++ {

        result *= i

    }

    return result

}

  

func permutation(n, r int) int {

    return factorial(n) / factorial(n-r)

}

  

func combination(n, r int) int {

    return factorial(n) / (factorial(r) * factorial(n-r))

}

  

func main() {

    var a, b, c, d int

    fmt.Print("Masukkan empat angka (a b c d): ")

    fmt.Scan(&a, &b, &c, &d)

  

    if a < c || b < d {

        fmt.Println("Input tidak valid: pastikan a >= c dan b >= d")

        return

    }

  

    fmt.Println(permutation(a, c), combination(a, c))

    fmt.Println(permutation(b, d), combination(b, d))

}

```
output
![[Cuplikan layar 2025-03-23 113209.png]]
## Soal2

``` go
package main

  

import "fmt"

  

func hitungSkor(waktu [8]int) (soal int, skor int) {

    for _, t := range waktu {

        if t < 301 {

            soal++

            skor += t

        }

    }

    return

}

  

func main() {

    var a string

    var b [8]int

    var pemenang string

    var maxSoal, minSkor int = 0, 301*8

  

    for {

        fmt.Print("Masukkan nama peserta dan waktu pengerjaan: ")

        fmt.Scan(&a)

        if a == "selesai" {

            break

        }

        for i := 0; i < 8; i++ {

            fmt.Scan(&b[i])

        }

        soal, skor := hitungSkor(b)

        if soal > maxSoal || (soal == maxSoal && skor < minSkor) {

            pemenang, maxSoal, minSkor = a, soal, skor

        }

    }

  

    fmt.Println("Pemenang:", pemenang, maxSoal, minSkor)

}
```


output
![[Cuplikan layar 2025-03-23 114502.png]]

## Soal3

``` go
package main

  

import "fmt"

  

func cetakDeret(n int) {

    for n != 1 {

        fmt.Print(n, " ")

        if n%2 == 0 {

            n /= 2

        } else {

            n = 3*n + 1

        }

    }

    fmt.Println(1)

}

  

func main() {

    var n int

    fmt.Print("Masukkan satu bilangan integer positif yang lebih kecil dari 1000000.: ")

    fmt.Scan(&n)

    if n <= 0 || n >= 1000000 {

        fmt.Println("Input tidak valid.")

        return

    }

    cetakDeret(n)

}
```

output
![[Cuplikan layar 2025-03-23 114731.png]]