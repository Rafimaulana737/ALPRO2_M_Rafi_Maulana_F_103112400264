## dasar teori
Go atau Golang diciptakan oleh Google yang dipelopori oleh Robert Griesemer, Rob Pike, dan Ken Thompson dan diumumkan kepada publik pada bulan November 2009. Bahasa pemrograman ini dirancang dengan tujuan untuk menjadi efisien dalam proses kompilasi dan eksekusi, serta efektif dalam menulis program yang dapat diandalkan . Dalam pengembangannya, Go menghindari fitur yang memperumit kode dan tidak dapat efisien, seperti halnya bahasa pemrograman C, sehingga Go dapat menghasilkan output yang optimal dengan waktu minimal. Fitur yang diandalkan dalam bahasa pemrograman ini antara lain konkurensi yang efisien dan pendekatan yang sangat fleksibel terhadap abstraksi data dan pemrograman berorientasi objek.

soal1

``` go
package main
import "fmt"

func main() {
    var (
        satu, dua, tiga string
        temp string
    )

    fmt.Print("Masukan input string: ")
    fmt.Scanln(&satu)

    fmt.Print("Masukan input string: ")
    fmt.Scanln(&dua)

    fmt.Print("Masukan input string: ")
    fmt.Scanln(&tiga)

    fmt.Println("Output awal = " + satu + " " + dua + " " + tiga)
    temp = satu
    satu = dua
    dua = tiga
    tiga = temp
    fmt.Println("Output akhir = " + satu + " " + dua + " " + tiga)
}

	Program ini di gunakan untuk menentukan faktor faktor dari bilangan yang dimasukkan user, lalu program akan cek apakah bilangan tersebut prima atau tidak. Program ini memakai metode perulangan untuk mencari faktor faktor dari bilangan tersebut.

```


soal2

``` go
package main
import "fmt"

func main() {
    var tahun int
    var kabisat bool

    fmt.Print("Masukkan tahun: ")
    fmt.Scan(&tahun)
  
    kabisat = (tahun % 400 == 0) || (tahun % 4 == 0 && tahun % 100 != 0)
    fmt.Println("kabisat: ", kabisat)
}
//Program ini menentukan apakah suatu tahun adalah tahun kabisat atau tidak. Tahun kabisat memenuhi salah satu dari dua kondisi:

// 1. Habis dibagi 400 **(tahun % 400 == 0)**
// 2. Habis dibagi 4 tetapi * tidak  habis dibagi 100 *(tahun % 4 == 0 && tahun % 100 != 0)**





```



SOAL3

``` go
package main
import "fmt"

func main() {
    var r float64
    const pi = 3.1415926535

    fmt.Print("Jarijari: ")
    fmt.Scan(&r)

    volume := (4.0 / 3.0) * pi * (r * r * r)
    luasPermukaan := 4 * pi * (r * r)

    fmt.Printf("Volume %.4f bola dan luas kulit %.4f\n", volume, luasPermukaan)
}


//Program ini menghitung volume dan luas permukaan bola berdasarkan jari jari (`r`) yang dimasukkan pengguna.


```

SOAL4
``` GO

Package main
import "fmt"

func main() {
    var celsius float64
    
    fmt.Print("Masukkan temperatur Celsius: ")
    fmt.Scan(&celsius)

    fahrenheit := (celsius * 9 / 5) + 32
    reamur := celsius * 4 / 5
    kelvin := (fahrenheit + 459.67) * 5 / 9

    fmt.Println("Temperatur dalam Reamur: ", reamur)
    fmt.Println("Temperatur dalam Fahrenheit: ", fahrenheit)
    fmt.Printf("Temperatur dalam Kelvin: %.0f\n", kelvin)
}


//Program ini mengonversi suhu dari Celsius ke Reamur, Fahrenheit, dan Kelvin**.



```

SOAL5

``` go
package main
import "fmt"
  
func main() {
    var angka1, angka2, angka3, angka4, angka5 int
    var huruf1, huruf2, huruf3 rune

    fmt.Scan(&angka1, &angka2, &angka3, &angka4, &angka5)
    fmt.Scanln()
    fmt.Scanf("%c%c%c\n", &huruf1, &huruf2, &huruf3)
  
    huruf1 += 1
    huruf2 += 1
    huruf3 += 1
  
    fmt.Printf("%c%c%c%c%c\n", angka1, angka2, angka3, angka4, angka5)
    fmt.Printf("%c%c%c\n", huruf1, huruf2, huruf3)
}

// Program ini digunakan untuk membaca lima bilangan bulat dan 3 karakter huruf yang di input oleh user. lima bilangan bulat tersebut akan di ubah menjadi huruf sehingga dapat menyusun sebuah kata tanpa spasi begitu juga dengan 3 karakter huruf. Program ini memanfaatkan tipe data rune untuk menangani karakter dan operasi aritmetika sederhana untuk menggeser nilai ASCII.

```

SOAL2_1
``` go
package main
import "fmt"
  
func main() {
    var warna1, warna2, warna3, warna4 string

    berhasil := true

    for i := 1; i <= 5; i++ {
        fmt.Print(" Percobaan ", i, " : ")
        fmt.Scan(&warna1, &warna2, &warna3, &warna4)

        if !(warna1 == "merah" && warna2 == "kuning" && warna3 == "hijau" && warna4 == "ungu") {

            berhasil = false
        }
    }
    fmt.Println("Berhasil:", berhasil)
}

//Program akan menganalisa apakah input dari user selalu sama dengan urutan yang ada di soal, program akan mengecek apakah setiap perulangan selalu sama. Jika program membaca warna merah, kuning, hijau dan ungu secara berurutan secara terus menerus maka output yang di hasilkan adalah true karna dari awal nilai dari "berhasil" adalah true dan jika warna berurutan atau ada yang tidak sesuai, maka akan false.

```


soal2_2
``` go
package main
import "fmt"
  
func main() {
    var bunga, pita string
    var jumlahBunga int

    for {
        fmt.Print("Bunga: ")
        fmt.Scan(&bunga)

        if bunga == "selesai" {
            break
        }

        if jumlahBunga > 0 {
            pita += " – " + bunga
        } else {
            pita += bunga
        }
        jumlahBunga++
    }

    fmt.Println("Pita:", pita)
    fmt.Println("Jumlah bunga:", jumlahBunga)
}
//Program ini adalah versi yang telah di modifikasi yakni ketika ingin menghentikan perulangan maka user harus mengetik "selesai" hal ini memakai konsep while-loop yakni ketika program menerima perintah untuk break maka program secara otomatis akan berhenti jika tidak maka program akan terus meminta dan akan di hitung ke dalam variabel "jumlah bunga" terus menerus sampai user merasa cukup.


```

SOAL2_3
``` GO

package main
import "fmt"

func main() {
    var kiri, kanan, berat float64
    var total = false
    for berat < 150 {

        fmt.Printf("Masukan berat belanjaan di kedua kantong ")
        fmt.Scanln(&kiri, &kanan)
        
        selisih := kiri - kanan
        if selisih < 0 {
            selisih = -selisih
        }

        total = selisih >= 9
        berat = kiri + kanan
        if berat < 150 {
            fmt.Println("Sepeda motor pak Andi akan oleng ", total)
        }
    }
    fmt.Println("Program selesai")
}
//Program akan memprediksi apakah berat dari motor pak andi telah mencapai maksimul, jika ya maka program akan otomatis berhenti, namun jika tidak maka program akan meminta jumlah berat kantong dari pak andi. program ini memkai looping untuk meminta user memasukkan jumlah berat secara terus menerus sampai target di penuhi dan memakai if untuk mengetahui apakah berat nya
```


SOAL2_4
``` GO
package main

import (
    "fmt"
    "math"
)

func main() {
    var k int
  
    fmt.Print("Nilai k = ")
    fmt.Scan(&k)

    result := 1.0
    for i := 0; i <= k; i++ {
        numerator := math.Pow(float64(4*i+2), 2)
        denumerator := float64((4*i + 1) * (4*i + 3))
        result *= numerator / denumerator
    }
    fmt.Print("Nilai akar 2 = ", result)
}
//Program ini menjalankan perhitungan matematika seperti pada soal. Program meminta pengguna untuk memasukkan nilai KKK sebagai input. Kemudian, program akan menghitung sesuai rumus dan menampilkan hasilnya, program ini menggunakan loop agar mudah menghitung hal tersebut secara ber ulang ulang



```


SOAL3_1
``` go
package main
import "fmt"

func main() {
    var berat int
    fmt.Print("Masukkan berat parsel (gram): ")
    fmt.Scanln(&berat)
  
    kg, gram := berat/1000, berat%1000
    biaya := kg * 10000
    tambahan := 0

    if kg < 10 {
        if gram < 500 {
            tambahan = gram * 15
        } else {
            tambahan = gram * 5
        }
    }

    fmt.Println("Berat parsel:", berat, "gram")
    fmt.Println("Total berat:", kg, "kg", gram, "gram")
    fmt.Println("Detail biaya: Rp.", biaya, "+ Rp.", tambahan)
    fmt.Println("Total biaya: Rp", biaya+tambahan)
 }
}

//PROGRMA INI MENGHITUNG BIAYA PENGIRIMAN PARSEL DALAM GRAM

```


SOAL3_2
``` go
package main
import "fmt"

func main() {
    var nam float64
    var nmk string
  
    fmt.Print("Nilai akhir mata kuliah: ")
    fmt.Scanln(&nam)

    if nam > 80 {
        nmk = "A"
    } else if nam > 72.5 && nam <= 80 {
        nmk = "AB"
    } else if nam > 65 && nam <= 72.5 {
        nmk = "B"
    } else if nam > 57.5 && nam <= 65 {
        nmk = "BC"
    } else if nam > 50 && nam <= 57.5 {
        nmk = "C"
    } else if nam > 40 && nam <= 50 {
        nmk = "D"
    } else if nam <= 40 {
        nmk = "E"
    }
    fmt.Println("Nilai mata kuliah:", nmk)

}

//program ini menghitung dan mengklopokan nilai yg di imput oleh pengimput dan mengklompokan data tersebut
```

SOAL3_3
``` go

package main

  

import "fmt"

  

func main() {

    var b int

    fmt.Print("Bilangan: ")

    fmt.Scan(&b)

  

    fmt.Print("Faktor: ")

    count := 0

    for i := 1; i <= b; i++ {

        if b%i == 0 {

            fmt.Print(i, " ")

            count++

        }

    }

    fmt.Println()

  

    if count == 2 {

        fmt.Println("Prima: true")

    } else {

        fmt.Println("Prima: false")

    }

}

//menghitung bilangan prima dangan cara memasukan rumus



```