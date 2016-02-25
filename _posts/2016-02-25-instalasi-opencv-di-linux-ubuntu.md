---
layout: post
title: Instalasi OpenCV di Linux Ubuntu

modified: 2016-02-25
tags: [opencv, linux, c++]
image:
  feature: butterfly-victoriya_.jpg
  credit: victoriya_


---
Halo semuanya, kali ini saya ingin berbagi cara bagaimana kita bisa menginstall OpenCV 2.4.9 di Linux.


Setelah mengotak-ngatik dan mengikuti beberapa tutorial tentang cara menginstall OpenCV 2.4.9 dari situs resminya, gagal, install ulang OS (tidak usah saya jelasin kenapa bisa sampai install ulang), akhirnya saya bisa juga menggunakan OpenCV 2.4.9 di Linux berbasis Ubuntu.



Jika kalian menggunakan Ubuntu pada versi-versi sebelumnya, kalian bisa mencoba menggunakan tutorial ini untuk menginstall OpenCV dan dependency-dependency-nya. Akan tetapi, setelah baca [tutorial oleh Dan Nguyen](http://danwin.com/2014/12/compile-opencv-2-4-10-ubuntu-14-04-14-10/), ternyata ada masalah antara OpenCV dengan ffmpeg. Setelah mengikuti tutorialnya, OpenCV sudah bisa digunakan.


Itu adalah cara pertama yang saya gunakan dan berhasil. Namun ternyata ada cara lebih mudah.


Repository Ubuntu sudah menyediakan beberapa library OpenCV yang bisa digunakan untuk melakukan operasi-operasi pemrosesan citra digital. Coba kalian buka ***Synaptic package manager*** (kalau belum ada, silahkan install melalui ubuntu software center) dan cari `opencv`. Install-lah package-package yang ditemukan.

<figure>
	<img src="/images/p_synaptic package manager opencv.png" alt="">
	<figcaption>Synaptic Package Manager - OpenCV</figcaption>
</figure>



Nah, untuk membuat program pemrosesan citra digital menggunakan OpenCV, install-lah ***Geany***. Geany adalah IDE yang kita bisa gunakan untuk membuat program C/C++ di Ubuntu. Silahkan cari dan install saja di Ubuntu Software Center.


> Note: Pastikan sudah menginstall C/C++ compiler, untuk mengecek silahkan buka terminal dan ketikkan perinta g++. Jika tidak ditemukan perintah tersebut, berarti kalian belum menginstall compilernya.


Setelah menginstall Geany dan C/C++ compiler, buatlah suatu direktori untuk menyimpan program kalian.


Buatlah sebuah fail cpp dan siapkan suatu citra di dalam direktori tersebut. Masukkan kodingan berikut di dalam fail cpp yang sudah kalian buat menggunakan ***Geany***.

{% highlight cpp %}
#include "iostream"
#include "opencv2/imgproc/imgproc.hpp"
#include "opencv2/core/core.hpp"
#include "opencv2/highgui/highgui.hpp"


using namespace std;
using namespace cv;

int main() {
 Mat image;// new blank image
    image = imread("image.jpeg");// read the file
    namedWindow( "Display window", CV_WINDOW_AUTOSIZE );// create a window for display.
    imshow( "Display window", image );// show our image inside it.
    waitKey(0);// wait for a keystroke in the window
    return 0;

}
{% endhighlight %}

Nah, sebelum kalian compile, kalian harus memberi tahu Geany untuk mengikutsertakan library OpenCV yang sudah kalian install sebelumnya ketika membuild program cpp kalian. Caranya adalah klik ***Set Build Command*** (klik tombol panah di samping icon batu bata). Di isian ***Build***, tambahkan ***\`pkg-config --libs opencv\`***.


Compile (F9) dan jalankan (F5) program kalian dan hasilnya akan seperti ini:

<figure>
	<img src="/images/p_opencv2.4.9 ubuntu 14.10.png" alt="">
	<figcaption>OpenCV 2.4.9 di Linux</figcaption>
</figure>

Sudah selesai deh,, gampang kn? :)


[Sumber](http://auriza.site40.net/notes/ubuntu/opencv-installation-on-ubuntu-1204/)
