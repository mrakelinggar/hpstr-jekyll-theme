---
layout: post
title: Mengembalikan Lebih Dari Satu Nilai di R
description: "...from a new Notes from a Newbie"
modified: 2016-03-11
tags: [R]

image:
  feature: programming-StockSnap.jpg
  credit: StockSnap
comments: yes
---

Sebelumnya saya sudah menulis [bagaimana caranya mengembalikan lebih dari satu nilai menggunakan  Python](http://mrakelinggar.github.io/python-mengembalikan-lebih-dari-satu-nilai/).

Kali ini saya ingin memposting bagaimana cara melakukan hal serupa di R.

<!--excerpt-->

Sama halnya di Python, caranya sangatlah sederhana di R. Akan tetapi ada sedikit perbedaan

Pada definisi fungsi di Python, cukup kalian beritahu untuk mengembalikan variabel-variabel yang ingin dikembalikan oleh fungsi. Akan tetapi di R tidak segampang itu, kalian harus menggabungkan variabel-variabel tersebut sebagai 'satu kesatuan'.

Untuk contoh, di postingan ini saya akan membuat fungsi yang akan mengembalikan rata-rata, standar deviasi, nilai maksimum, dan nilai minimum.

{% highlight r %}

getValues <- function(x) {
  avg <- mean(x)
  stddev <- sd(x)
  maximum <- max(x)
  minimum <- min(x)

  return (list(average = avg, stddev = stddev, maximum = maximum, minimum = minimum))
}

x = c(1,2,3,4,5,6,7,8,9,10)

values <- getValues(x)

print (sprintf("Average: %f", values$average))
print (sprintf("Std dev: %f", values$stddev))
print (sprintf("Maximum: %f", values$maximum))
print (sprintf("Minimum: %f", values$minimum))

{% endhighlight %}

Hasil dari program di atas adalah:

{% highlight console %}

> source('~/Projects/blog/funcR/temp.R', echo=FALSE)
[1] "Average: 5.500000"
[1] "Std dev: 3.027650"
[1] "Maximum: 10.000000"
[1] "Minimum: 1.000000"

{% endhighlight %}

>Hal yang mungkin perlu diketahui di sini adalah...<br/>Fungsi dari **Numpy di Python** menghitung standar deviasi **populasi** (lihat [dokumentasinya](http://docs.scipy.org/doc/numpy-1.10.0/reference/generated/numpy.std.html))<br/>Fungsi bawaan **R** menghitung standar deviasi **sampel** (lihat di [sini](http://stats.stackexchange.com/questions/25956/what-formula-is-used-for-standard-deviation-in-r))

Itulah mengapa nilai standar deviasi hasil program R dan Python berbeda (lihat saja di postingan saya yang <a href="http://mrakelinggar.github.io/python-mengembalikan-lebih-dari-satu-nilai/">sebelumnya</a>.

Sudah, itu saja. gampang juga kan?
