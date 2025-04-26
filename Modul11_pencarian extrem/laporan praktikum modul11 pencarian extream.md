## Dasar teori
Pencarian secara sekuensial ini adalah pencarian yang dilakukan dari data pertama, kedua hingga terakhir secara satu persatu dan berurutan. Ciri khas dari pencarian ini adalah proses pencarian akan berhenti ketika data yang dicari ditemukan, walaupun masih terdapat data yang belum dicek nilainya. Algoritma ini dikenal dengan nama Sequential Search, karena prosesnya melakukan pengecekan setiap elemen array secara satu persatu dan sekuensial dari data pertama hingga ditemukan atau data terakhir. Binary Search adalah: (dengan asumsi data terurut dari kecil membesar (ascending), dan data dengan indeks kecil ada di "kiri" dan indeks besar ada di "kanan")

1. Ambil salah satu data dalam rentang data yang ada, algoritma di bawah menggunakan rentang dari kiri 𝒌𝒓 s.d. kanan 𝒌𝒏. Untuk kemudahan dan alasan lainnya, biasanya yang diambil adalah paling tengah dalam rentang tersebut.
    
2. Jika data terambil tersebut terlalu kecil, maka ubah/geser rentang data ke sebelah kanan posisi data tersebut. Ini karena jika data terambil terlalu kecil, maka semua data sebalah kirinya juga akan terlalu kecil dari yang ingin dicari.
    
3. Begitu juga sebaliknya jika data terambil terlalu besar.

## Guided

## Soal1
sebuah toko memiliki daftar nama barang sebanyak n buah. setiap barang disimpan dalam array berisi string. buatlah program untuk mencari apakah nama barang yg dicari (X) tersedia di toko atau tidak. pencarian dilakukan menggunkan sequential seaerch.program mengembalikan true jika barang ditemukan, atu false jika tidak ditemukan
``` go

package main

  

import "fmt"

  

func cariBarang(daftarBarang []string, x string) bool {

    for _, barang := range daftarBarang {

        if barang == x {

            return true

        }

    }

    return false

}

  

func main() {

    var n int

    var x string

  

    fmt.Print("Masukkan jumlah barang: ")

    fmt.Scan(&n)

  

    daftarBarang := make([]string, n)

    fmt.Println("Masukkan nama barang:")

    for i := 0; i < n; i++ {

        fmt.Scan(&daftarBarang[i])

    }

  

    fmt.Print("Masukkan nama barang yang dicari: ")

    fmt.Scan(&x)

  

    if cariBarang(daftarBarang, x) {

        fmt.Println("true")

    } else {

        fmt.Println("false")

    }

}
```

## output

![[guided1.png]]

## Soal2
Buat program untuk membaca sebuah kalimat (string) dan sebuah karakter yang ingin dicari gunakan sequential search untuk mencari apakah karakter tersebut terdapat di dalam kalimat jika ya, tampilkann semua posisi (indeks) karakter tersebut di kalimat.

``` go
package main

  

import "fmt"

  

func main() {

    kalimat := "algoritma pemrograman"

    karakter := 'g'

  

    var indeks []int

  

    for i, c := range kalimat {

        if c == karakter {

            indeks = append(indeks, i)

        }

    }

  

    if len(indeks) > 0 {

        fmt.Print("Karakter ditemukan pada indeks : ")

        for i, idx := range indeks {

            if i > 0 {

                fmt.Print(", ")

            }

            fmt.Print(idx)

        }

        fmt.Println()

    } else {

        fmt.Println("Karakter tidak ditemukan.")

    }

}

```
## Output
![[guided2.png]]
## Soal3 

diketahui array mahasiswa terdiri atas n data bertipe sturct yang menyimpan data nama dan nim mahasisiwa . array sudah terurut membesar bedsasarkan nim.buatlah program ntuk mencari nim tertentu engunakan algoritma binary search dan mengembalikan indeks  dari nim tersebut 
``` go
package main

import "fmt"

type Mahasiswa struct {
    nama string
    nim  string
}

func binarySearch(data []Mahasiswa, x string) int {
    low := 0
    high := len(data) - 1

    for low <= high {
        mid := (low + high) / 2

        if data[mid].nim == x {
            return mid
        } else if data[mid].nim < x {
            low = mid + 1
        } else {
            high = mid - 1
        }
    }

    return -1
}

func main() {
    mahasiswa := []Mahasiswa{
        {"Andi", "220001"},
        {"Budi", "220002"},
        {"Citra", "220003"},
        {"Dina", "220004"},
    }

    X := "220003"
    index := binarySearch(mahasiswa, X)

    if index != -1 {
        fmt.Println("Indeks mahasiswa ditemukan:", index)
    } else {
        fmt.Println("NIM tidak ditemukan.")
    }
}

```
## Output
![[guided3.png]]



## UNGUIDED

## Soal1

``` go
package main

  

import "fmt"

  

type Calon struct {

    nomor, suara int

}

  

func sequentialSearch(arr []Calon, n int, x int) int {

    for i := 0; i < n; i++ {

        if arr[i].nomor == x {

            return i

        }

    }

    return -1

}

  

func main() {

    var suaraMasuk, suaraSah, x int

    var daftar []Calon

  

    fmt.Println("Masukkan suara :")

    for {

        fmt.Scan(&x)

        if x == 0 {

            break

        }

  

        if x >= 1 && x <= 20 {

            suaraSah++

            pos := sequentialSearch(daftar, len(daftar), x)

            if pos != -1 {

                daftar[pos].suara++

            } else {

                daftar = append(daftar, Calon{nomor: x, suara: 1})

            }

        }

        suaraMasuk++

    }

  

    fmt.Println("Suara masuk :", suaraMasuk)

    fmt.Println("Suara sah :", suaraSah)

    for i := 0; i < len(daftar); i++ {

        fmt.Println(daftar[i].nomor, ":", daftar[i].suara)

    }

}

```
## Output
![[unguided1.png]]

## Soal2
``` go
package main

  

import "fmt"

  

func main() {

    input := []int{7, 19, 3, 2, 78, 3, 1, -3, 18, 69, 0}

    var suaraMasuk, suaraSah int

    var count [21]int

  

    for i := 0; i < len(input); i++ {

        if input[i] == 0 {

            break

        }

        suaraMasuk++

        if input[i] >= 1 && input[i] <= 20 {

            count[input[i]]++

            suaraSah++

        }

    }

  

    k1, k2 := 0, 0

    for i := 1; i <= 20; i++ {

        if count[i] > count[k1] || (count[i] == count[k1] && i < k1) {

            k2 = k1

            k1 = i

        } else if count[i] > count[k2] || (count[i] == count[k2] && i < k2 && i != k1) {

            k2 = i

        }

    }

  

    fmt.Println("Suara masuk:", suaraMasuk)

    fmt.Println("Suara sah:", suaraSah)

    fmt.Println("Ketua RT:", k1)

    fmt.Println("Wakil ketua:", k2)

}
```
## Output
![[unguided2.png]]

## Soal3
```go
package main

  

import "fmt"

  

const NMAX = 1000000

var data [NMAX]int

  

func main() {

    var n, k int

    fmt.Scan(&n, &k)

  

    isiArray(n)

    idx := posisi(n, k)

  

    if idx != -1 {

        fmt.Println(idx)

    } else {

        fmt.Println("TIDAK ADA")

    }

}

  

func isiArray(n int) {

    for i := 0; i < n; i++ {

        fmt.Scan(&data[i])

    }

}

  

func posisi(n, k int) int {

    return binarySearch(data[:n], n, k)

}

  

func binarySearch(arr []int, n, x int) int {

    kiri, kanan := 0, n-1

  

    for kiri <= kanan {

        mid := (kiri + kanan) / 2

        if x < arr[mid] {

            kanan = mid - 1

        } else if x > arr[mid] {

            kiri = mid + 1

        } else {

            return mid

        }

    }

    return -1

}
```

## Output
![[unguided3.png]]