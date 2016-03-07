---
layout: post
title: Mengembalikan Lebih Dari Satu Nilai di Python
description: "...from a new Notes from a Newbie"
modified: 2016-03-08
tags: [Python]

image:
  feature: programming-StockSnap.jpg
  credit: StockSnap
comments: yes
---

Salah satu kelebihan yang ditawarkan oleh bahasa pemrograman Python dibanding beberapa bahasa pemrograman lainnya adalah kemampuan fungsi (`function`) untuk mengembalikan lebih dari satu nilai.

<!--excerpt-->

Caranya sangatlah sederhana.

Pada definisi fungsi anda, cukup kalian beritahu untuk mengembalikan variabel-variabel yang ingin dikembalikan oleh fungsi.

Untuk contoh, di postingan ini saya akan membuat fungsi yang akan mengembalikan rata-rata, standar deviasi, nilai maksimum, dan nilai minimum.

{% highlight python %}
import numpy as np

def getValues(x):
    avg = np.mean(x)
    stddev = np.std(x)
    maximum = max(x)
    minimum = min(x)

    return avg, stddev, maximum, minimum #kembalikan nilai-nilainya

x = [1,2,3,4,5,6,7,8,9,10]

avg, stddev, maximum, minimum = getValues(x)

print "Average: ", avg
print "Std dev: ", stddev
print "Maximum: ", maximum
print "Minimum: ", minimum

{% endhighlight %}

Hasil dari program di atas adalah:

{% highlight console %}

Average:  5.5
Std dev:  2.87228132327
Maximum:  10
Minimum:  1
[Finished in 0.132s]

{% endhighlight %}

Sudah, itu saja. gampang sekali bukan? Ini adalah salah satu alasan kenapa saya menyukai Python, **sangat memudahkan programmer**.
