
---
Pengantar Skema Pemrosesan Sekuensial yang dipersenjatai bentuk perulangan dan bentuk percabangan, banyak problem komputasi yang dapat diselesaikan. Dengan cara ini data dapat dibaca, dianalisis, dan diproses secara bertahap sesuai urutan kemunculannya.

---
## guided

``` go
package main
import "fmt"

func bubbleSort(arr []int) int {
    swapCount := 0
    n := len(arr)
    for i := 0; i < n-1; i++ {
        for j := 0; j < n-1-i; j++ {
            if arr[j] > arr[j+1] {
                arr[j], arr[j+1] = arr[j+1], arr[j]
                swapCount++
            }
        }
    }
    return swapCount
}

func main() {
    nilai := []int{75, 60, 90, 85, 70}
    fmt.Println("sebelum diurutkan:", nilai)
    jumlahSwap := bubbleSort(nilai)
    fmt.Println("setelah diurutkan :", nilai)
    fmt.Println("Jumlah pertukaran      :", jumlahSwap)
}

```

![[modul17_skema relasi/output/guided1.png]]
#### penjelasan 
Program ini mengurutkan nilai ulangan teman Aldi menggunakan metode Bubble Sort, yaitu dengan membandingkan pasangan nilai yang berdekatan dan menukarnya. Proses ini diulang hingga seluruh nilai tersusun dari yang terkecil ke terbesar. Selain itu, program juga menghitung dan menampilkan jumlah pertukaran "swap" yang terjadi selama proses pengurutan.


## unguided

## soal1
``` go
package main

import "fmt"

  

func main() {

    var angka, total float64

    var jumlah int

  

    for {

        fmt.Scanln(&angka)

        if angka == 9999 {

            break

        }

        total += angka

        jumlah++

    }

  

    if jumlah == 0 {

        fmt.Println("Masukkan angka selain 9999")

    } else {

        rerata := total / float64(jumlah)

        fmt.Printf("Rerata dari data: %.2f\n", rerata)

    }

}
```

![[modul17_skema relasi/output/unguided1.png]]
**penjelasan program**
Program ini menghitung rata-rata dari sekumpulan bilangan real yang diakhiri dengan marker 9999. Selama input bukan 9999 maka bilangan akan dijumlahkan dan jumlah data dihitung. Setelah marker dimasukkan, program akan menghitung dan menampilkan rata-rata.

## soal2

``` go
package main

  

import "fmt"

  

func main() {

  

    var x string

    var n int

  

    fmt.Print("Masukkan string x: ")

    fmt.Scan(&x)

  

    fmt.Print("Masukkan jumlah data string n: ")

    fmt.Scan(&n)

  

    strings := make([]string, n)

    fmt.Println("Masukkan", n, "string:")

  

    for i := 0; i < n; i++ {

        fmt.Printf("Data ke-%d: ", i+1)

        fmt.Scan(&strings[i])

    }

  

    found := false

    for _, s := range strings {

        if s == x {

            found = true

            break

        }

    }

    fmt.Println("a. Apakah string x ada dalam kumpulan data?", found)

  

    pos := -1

    for i, s := range strings {

        if s == x {

            pos = i + 1

            break

        }

    }

    if pos != -1 {

        fmt.Println("b. String x ditemukan pada posisi ke:", pos)

    } else {

        fmt.Println("b. String x tidak ditemukan.")

    }

  

    count := 0

    for _, s := range strings {

        if s == x {

            count++

        }

    }

    fmt.Println("c. Jumlah kemunculan string x:", count)

  

    if count >= 2 {

        fmt.Println("d. Ya, string x muncul setidaknya dua kali.")

    } else {

        fmt.Println("d. Tidak, string x tidak muncul dua kali atau lebih.")

    }

}

```
output
![[unguided2.go.png]]
## penjelasan program
Program ini berfungsi untuk memeriksa keberadaan sebuah string x dalam sekumpulan data string yang dimasukkan oleh pengguna, serta menampilkan beberapa informasi terkait string tersebut. Program dimulai dengan meminta input string x dan jumlah data string n, lalu membuat slice untuk menampung n string yang dimasukkan pengguna. Setelah itu, program memeriksa apakah string x ada dalam kumpulan data, mencetak hasilnya sebagai nilai benar atau salah. Kemudian, program mencari posisi pertama kemunculan string x dan mencetak posisinya jika ditemukan. Selanjutnya, program menghitung berapa kali string x muncul dalam data dan menampilkan jumlah tersebut. Terakhir, program memeriksa apakah string x muncul setidaknya dua kali dan mencetak pernyataan yang sesuai. Program ini memperlihatkan penggunaan slice, perulangan, dan percabangan dalam pengolahan data string.

## soal3
``` go
package main
import (
    "fmt"
    "math/rand"
    "time"
)

func main() {
    var jumlahTetes int
    var countA, countB, countC, countD int

    fmt.Scan(&jumlahTetes)
  
    rand.Seed(time.Now().UnixNano())
  
    for i := 0; i < jumlahTetes; i++ {
        x := rand.Float64()
        y := rand.Float64()

        if x < 0.5 && y >= 0.5 {
            countA++
        } else if x >= 0.5 && y >= 0.5 {
            countB++
        } else if x < 0.5 && y < 0.5 {
            countC++
        } else if x >= 0.5 && y < 0.5 {
            countD++
        }
    }
  
    ukuranTetesan := 0.0001
    curahA := float64(countA) * ukuranTetesan
    curahB := float64(countB) * ukuranTetesan
    curahC := float64(countC) * ukuranTetesan
    curahD := float64(countD) * ukuranTetesan

    fmt.Printf("Curah hujan daerah A: %.4f milimeter\n", curahA)
    fmt.Printf("Curah hujan daerah B: %.4f milimeter\n", curahB)
    fmt.Printf("Curah hujan daerah C: %.4f milimeter\n", curahC)
    fmt.Printf("Curah hujan daerah D: %.4f milimeter\n", curahD)
}


```
## OUTPUT
![[modul17_skema relasi/output/unguided3.png]]
## penjelasan program
**-Penjelasan Program-** Program ini mensimulasikan tetesan air hujan yang jatuh secara acak di bidang koordinat dari titik (0,0) hingga (1,1), kemudian menghitung banyaknya tetesan yang jatuh di empat daerah A, B, C, dan D berdasarkan posisi kuadran koordinat. Titik-titik acak dihasilkan menggunakan "rand.Float64()", dan setiap titik diklasifikasikan ke salah satu daerah berdasarkan nilai "x" dan "y". Setelah semua titik dihitung, program mengalikan jumlah tetesan di masing-masing daerah dengan 0.0001 untuk mengubahnya ke satuan milimeter, lalu mencetak curah hujan untuk setiap daerah

## soal4
``` go
package main

  

import "fmt"

  

func main() {

  

    pi := 0.0

    prevPi := 0.0

    i := 0

  

    for {

        term := 1.0 / float64(2*i+1)

        if i%2 == 1 {

            term = -term

        }

        pi += term

  

        piTimes4 := pi * 4

        prevPiTimes4 := prevPi * 4

  

        diff := piTimes4 - prevPiTimes4

        if diff < 0 {

            diff = -diff

        }

  

        if i > 0 && diff < 0.00001 {

            fmt.Printf("Hasil PI: %.9f\n", prevPiTimes4)

            fmt.Printf("Hasil PI: %.9f\n", piTimes4)

            fmt.Printf("Pada i ke: %d\n", i)

            break

        }

  

        prevPi = pi

        i++

    }

}

```
OUTPUT
![[UNGUIDED4.png]]
## penjelasan program
Program ini menghitung nilai π menggunakan deret Leibniz dengan menjumlahkan suku ke-i dari bentuk Si=(−1)i+1/(2i−1) untuk "n" suku pertama. Setelah itu, program dimodifikasi untuk menghentikan perhitungan saat dua nilai π berturut-turut memiliki selisih kurang dari 0.00001. Nilai π dihitung dengan mengalikan total jumlah deret dengan 4, dan hasil dua nilai terakhir serta iterasi keberapa π dianggap konvergen ditampilkan sebagai output.

## soal5
``` go
package main

  

import (

    "fmt"

    "math"

    "math/rand"

    "time"

)

  

func main() {

    var jumlahTopping int

    fmt.Print("Masukkan jumlah topping: ")

    fmt.Scan(&jumlahTopping)

  

    rand.Seed(time.Now().UnixNano())

  

    dalamPizza := 0

    for i := 0; i < jumlahTopping; i++ {

        x := rand.Float64()

        y := rand.Float64()

        if math.Pow(x-0.5, 2)+math.Pow(y-0.5, 2) <= 0.25 {

            dalamPizza++

        }

    }

  

    pi := 4.0 * float64(dalamPizza) / float64(jumlahTopping)

  

    fmt.Printf("Banyak Topping: %d\n", jumlahTopping)

    fmt.Printf("Topping pada Pizza: %d\n", dalamPizza)

    fmt.Printf("PI : %.10f\n", pi)

}
```
## OUTPUT
![[unguided5.png]]
Penjelasan Program
program ini menggunakan metode Monte Carlo untuk memperkirakan nilai pi berdasarkan simulasi peletakan topping secara acak di atas pizza berbentuk lingkaran. Program meminta input dari pengguna untuk jumlah topping yang akan dijatuhkan secara acak. Fungsi rand.Float64() digunakan untuk menghasilkan angka acak antara 0 dan 1 yang mewakili posisi x dan y dari topping di atas bidang persegi satuan. Pusat lingkaran pizza ditempatkan di koordinat (0.5, 0.5) dengan jari-jari 0.5, sehingga titik berada di dalam lingkaran jika memenuhi persamaan (x-0.5)^2 + (y-0.5)^2 <= 0.25. Setiap kali topping jatuh di dalam lingkaran, variabel dalamPizza dihitung. Setelah selesai, nilai pi diperkirakan dengan rumus pi = 4 * (dalamPizza / jumlahTopping), yang didasarkan pada perbandingan antara jumlah topping yang jatuh di dalam pizza dengan total topping yang dijatuhkan. Hasilnya kemudian dicetak di layar, termasuk jumlah topping, topping yang jatuh di dalam pizza, dan nilai pi yang diperkirakan. Program ini adalah contoh penerapan simulasi acak untuk memperkirakan nilai matematika.