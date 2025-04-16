## Dasar teori
Pencarian adalah suatu proses yang lazim dilakukan di dalam kehidupan sehari-hari. Contoh penggunaannya dalam kehidupan nyata sangat beragam, misalnya pencarian file di dalam directory komputer, pencarian suatu teks di dalam sebuah dokumen, pencarian buku pada rak buku, dan contoh lainnya. Pertama pada modul ini akan dipelajari salah satu algoritma pencarian nilai terkecil atau terbesar pada sekumpulan data, atau biasa disebut pencarian nilai ekstrim


## Soal1
``` go
package main

  

import "fmt"    

  

func main(){

    var n int

    fmt.Print("MASUKAN ANAK KELICINYA COK!!!")

    fmt.Scanln(&n)

  

    for n <= 0 || n > 100 {

        fmt.Print("MASUKAN ANAK KELICINYA HARUS 1-100")

        return

    }

  

    berat := make([]float64, n)

    fmt.Println("Berat anak kelinci:")

    for i := 0; i < n; i++ {

        fmt.Printf("Kelinci %d: ", i+1)

        fmt.Scanln(&berat[i])

    }

  

    min := berat[0]

    max := berat[0]

  

    for i := 1; i < n; i++ {

        if berat[i] < min {

            min = berat[i]

        }

        if berat[i] > max {

            max = berat[i]

        }

    }

  

    fmt.Printf("Berat terkecil: %.2f\n", min)

    fmt.Printf("Berat terbesar: %.2f\n", max)

}
```

## Output
![[Cuplikan layar 2025-04-16 185014.png]]


## Soal2

``` go
package main

  

import "fmt"

  

func main() {

    var x, y int

    var beratIkan [1000]float64

  

    fmt.Print("MASUKKAN JUMLAH IKAN DAN JUMLAH IKAN DI WADAH: ")

    fmt.Scan(&x, &y)

  

    fmt.Println("MASUKKAN BERAT IKAN:")

    for i := 0; i < x; i++ {

        fmt.Scan(&beratIkan[i])

    }

  

    var totalBeratWadah []float64

    for i := 0; i < x; i += y {

        total := 0.0

        for j := i; j < i+y && j < x; j++ {

            total += beratIkan[j]

        }

        totalBeratWadah = append(totalBeratWadah, total)

    }

  

    fmt.Println("TOTAL BERAT IKAN DI SETIAP WADAH:")

    for _, berat := range totalBeratWadah {

        fmt.Println(berat)

    }

    fmt.Println()

  

    totalBerat := 0.0

    for _, berat := range totalBeratWadah {

        totalBerat += berat

    }

    rataRata := totalBerat / float64(len(totalBeratWadah))

    fmt.Printf("RATA-RATA BERAT IKAN DI SETIAP WADAH: %.2f\n", rataRata)

}
```


## Output

![[Cuplikan layar 2025-04-16 185239.png]]

## Soal3
``` go
package main

  

import "fmt"

  

// Tipe data array untuk berat balita

type arrBalita [100]float64

  

// Subprogram untuk menghitung berat minimum dan maksimum

func hitungMinMax(arrBerat arrBalita, n int, bMin, bMax *float64) {

    *bMin = arrBerat[0]

    *bMax = arrBerat[0]

    for i := 1; i < n; i++ {

        if arrBerat[i] < *bMin {

            *bMin = arrBerat[i]

        }

        if arrBerat[i] > *bMax {

            *bMax = arrBerat[i]

        }

    }

}

  

// Subprogram untuk menghitung rata-rata berat balita

func rerata(arrBerat arrBalita, n int) float64 {

    total := 0.0

    for i := 0; i < n; i++ {

        total += arrBerat[i]

    }

    return total / float64(n)

}

  

func main() {

    var n int

    var arrBerat arrBalita

    var bMin, bMax float64

  

    // Meminta input jumlah balita

    fmt.Print("Masukkan jumlah balita: ")

    fmt.Scan(&n)

  

    // Meminta input berat balita

    fmt.Println("Masukkan berat balita (dalam kg):")

    for i := 0; i < n; i++ {

        fmt.Scan(&arrBerat[i])

    }

  

    // Menghitung berat minimum, maksimum, dan rata-rata

    hitungMinMax(arrBerat, n, &bMin, &bMax)

    rataRata := rerata(arrBerat, n)

  

    // Menampilkan hasil

    fmt.Printf("Berat terkecil: %.2f kg\n", bMin)

    fmt.Printf("Berat terbesar: %.2f kg\n", bMax)

    fmt.Printf("Rata-rata berat: %.2f kg\n", rataRata)

}
```

## Output
![[Cuplikan layar 2025-04-16 185359.png]]