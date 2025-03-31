## DASAR TEORI
Rekursif secara sederhana dapat diartikan sebagai cara menyelesaikan suatu masalah dengan cara menyelesaikan sub-masalah yang identik dari masalah utama.

Teknik rekursif ini merupakan salah satu alternatif untuk mengganti struktur kontrol perulangan dengan memanfaatkan subprogram. • Base-case adalah kondisi proses rekursif berhenti. Base-case merupakan hal terpenting dan pertama yang harus diketahui ketika akan membuat program rekursif. Mustahil membuat program rekursif tanpa mengetahui base-case terlebih dahulu. • Recursive-case adalah kondisi dimana proses pemanggilan dirinya sendiri dilakukan. Kondisi recursive-case adalah komplemen atau negasi dari base-case. • Setiap algoritma rekursif selalu memiliki padanan dalam bentuk algoritma interatif.

Algoritma rekursif terdiri dari dua komponen utama: • Base-case (Basis), yaitu bagian untuk menghentikan proses rekursif dan menjadi komponen terpenting di dalam sebuah rekursif. • Recursive-case, yaitu bagian pemanggilan subprogramnya.

## soal1
```go
package main

import "fmt"

func main(){

    cetak(5)

  

}

func cetak(x int) {

  

if x == 666{

    fmt.Println(x)

}else{

    cetak(x+1)

    fmt.Println(x)

}

}

```

![[output1.png]]
## soal2
```go
package main

import "fmt"

func printStars(n int) {

    if n == 0 {

        return

    }

    fmt.Print("*")

    printStars(n - 1)

}
func printPattern(n, current int) {

    if current > n {

        return
    }

    printStars(current)

    fmt.Println()

    printPattern(n, current+1)

}
func main() {

    var n int

    fmt.Print("Masukkan nilai N: ")

    fmt.Scan(&n)

    printPattern(n, 1)

}
```

![[output2.png]]
## soal3
```go
package main
  
import "fmt"

func printStars(n int) {
    if n == 0 {

        return

    }

    fmt.Print("*")

    printStars(n - 1)

}
func printPattern(n, current int) {

    if current > n {

        return

    }

    printStars(current)

    fmt.Println()

    printPattern(n, current+1)

}
func main() {

    var n int

    for {

        fmt.Print("Masukkan nilai N (negative number to exit): ")

        fmt.Scan(&n)

        if n < 0 {

            fmt.Println("Exiting the program.")

            break

        }
        printPattern(n, 1)
        fmt.Println()
    }

}
```

![[output3.png]]

## soal4
```go
package main

import "fmt"

func tampilkanBarisan(n, awal int) {

    fmt.Print(n, " ")

    if n > 1 {

        tampilkanBarisan(n-1, awal)

        fmt.Print(n, " ")

    }

}

  

func main() {

    var n int

    fmt.Print("Masukkan bilangan: ")

    fmt.Scan(&n)

    tampilkanBarisan(n, n)

    fmt.Println()

}
```


![[output4.png]]

## soal5
```go
package main

import "fmt"

func printOddNumbers(n, current int) {

    if current > n {

        return

    }

    fmt.Print(current, " ")

    printOddNumbers(n, current+2)

}

func main() {

    var n int

    fmt.Print("Masukkan bilangan N: ")

    fmt.Scan(&n)

  

    if n < 1 {

        fmt.Println("Harap masukkan bilangan positif lebih dari 0.")

        return

    }

  

    fmt.Print("Bilangan ganjil dari 1 hingga ", n, ": ")

    printOddNumbers(n, 1)

    fmt.Println()

}
```

![[output5.png]]
## soal6
``` go
package main

import "fmt"

func pangkat(x, y int) int {

    if y == 0 {

        return 1

    }

    return x * pangkat(x, y-1)

}

  

func main() {

    var x, y int

    fmt.Print("Masukkan bilangan : ")

    fmt.Scan(&x)

    fmt.Print("Masukkan pangkat: ")

    fmt.Scan(&y)

    fmt.Printf("Hasil %d^%d = %d\n", x, y, pangkat(x, y))

}

```

![[output6.png]]