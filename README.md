# FLUTTER CODE PUSH SHOREBIRD

## A. PENGENALAN

### Apa itu Code Push

Code Push adalah suatu mekanisme yang digunakan dalam pemngembangan aplikasi mobile untuk melakukan pembaruan kode (code update) pada aplikasi yang telah diinstal di device penguna tanpa melalui proses release melalui PlayStore atau AppStore. Dengan Code Push, developer dapat mengirimkan dan menerapkan pembaruan code secara langsung ke device pengguna, sehingga memungkinkan perbaikan bug, improvement atau penambahan fitur tanpa harus melalui prosess distribusi dan permintaan review dari PlayStore atau AppStore.

Code Push memungkinkan developer untuk memperbarui code app secara dinamis dengan mengirim file update ke device sehingga memberikan kemudahan kepada developer dalam melakukan pembaruan aplikasi ataupun bug fixing tanpa harus user mengunduh ulang aplikasi.

Code Push juga memungkinkan developer untuk mengelola update code berdasarkan group pengguna atau segmentasi, sehingga memungkinkan pengembang untuk menguji pembaruan secara bertahap atau menyediakan fitur eksperimental (UAT / SIT) sebelum dilakukan release secara publish.

Dengan menggunakan Code Push, developer dapat meningkatkan fleksibilitas, efesiensi dan kecepatan dalam memperbarui aplikasi tanpa tergantung pada release dan persetujuan dari AppStore atau PlaySyore. Namun, penting untuk menggunakan Code Push dengan hati-hati dan memperhatikan keamanan dan kestabilan code pembaruan yang akan dikirimkan kepada pengguna.

### Apa itu Shorebird

Shorebird adalah sebuah library atau modul yang digunakan untuk mengelola dan memfasilitasi proses pembaruan code (Code Push) pada aplikasi berbasis Shorebird. Shorebird merupakan platform digunakan dalam pengembangan aplikasi cross-platform yang menggunakan teknologi web, seperti React Native, Flutter atau Cordova. 

Namun sampai dokumen ini ditulis (3 July 2023) shorebird masih belum disupport, di official websitenya masih berstatus “[iOS launching July 2023](https://shorebird.dev/#newsletter)”. Namun berdasarkan informasi dari komunitas pihak shorebird akan merelease preview support iOS pada July ini dan akan launching sepenuhnya bersama fitur android pada bulan September mendatang.

# B. INSTALASI

## Install Shorebird

Untuk menginstall command line interface (CLI) shorebird: 

Requirement: git

### Mac / Linux

Buka terminal dan run:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash
curl --proto '=https' --tlsv1.2 https://raw.githubusercontent.com/shorebirdtech/install/main/install.sh -sSf | bash
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

setelah installasi berhasil jalankan code beikut untuk memastikan shorebird terinstall:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash
$ shorebird
The shorebird command-line tool

Usage: shorebird <command> [arguments]

Global options:
-h, --help            Print this usage information.
-v, --version         Print the current version.
    --[no-]verbose    Noisy logging, including all shell commands executed.

Available commands:
  account        Manage your Shorebird account.
  apps           Manage your Shorebird apps.
  build          Build a new release of your application.
  cache          Manage the Shorebird cache.
  doctor         Show information about the installed tooling.
  init           Initialize Shorebird.
  login          Login as a new Shorebird user.
  logout         Logout of the current Shorebird user
  patch          Publish new patches for a specific release to Shorebird.
  release        Builds and submits your app to Shorebird.
  run            Run the Flutter application.
  subscription   Manage your Shorebird subscription.
  upgrade        Upgrade your copy of Shorebird.

Run "shorebird help <command>" for more information about a command.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Jika output sudah sesuai dengan pesan diatas maka shorebird telah berhasil terinstal. 

Untuk memastikan set-up shorebird jalankan perintah berikut:


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash

shorebird doctor
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Jika set-up sudah benar maka akan keluar pesan sebagai berikut: 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash
$ shorebird doctor

Shorebird v0.0.8
Shorebird Engine • revision d470ae25d21f583abe128f7b838476afd5e45bde

✓ Shorebird is up-to-date (0.7s)
✓ Flutter install is correct (0.1s)
✓ AndroidManifest.xml files contain INTERNET permission (26ms)

No issues detected!
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Sebaliknya apa bila shorebird belum berhasil set-up maka akan tampil pesan error, contoh sebagai berikut:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash
$ shorebird doctor 

Shorebird v0.8.0
Shorebird Engine • revision 6c1f35b941ba46596b88674cbb7c59ac3eff1119
✓ Shorebird is up-to-date (0.8s)
✗ Flutter install is correct (7.4s)
  [✗] Failed to determine path Flutter version. FlutterValidationException: Flutter version check did not complete successfully. /bin/sh: flutter: command not found


1 issue detected.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Dari pesan diatas menunjukan bahwa shorebird menemukan issue yaitu flutter belum sesuai, ini terjadi karena flutter belum terinstall atau karena menggunakan flutter manager seperti FVM. 


Untuk menangani issue ini perlu dilakukan instalasi flutter secara global. Jika anda menggunakan FVM maka disarankan untuk menguninstal FVM.

# C. ACCOUNT

Ketika shorebird terlah terinstall, anda perlu membuat akun terlebih dahulu apa bila memiliki akun di shorebird. 

## Sign-Up

Untuk membuat akun, jalankan perintah berikut: 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash	
shorebird account create
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

contoh Ketika berhasil:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash
❯ shorebird account create                                                                                                                         
Shorebird currently requires a Google account for authentication. If you'd like to use a different kind of auth, please let us know: https://github.com/shorebirdtech/shorebird/issues/335.

Follow the link below to authenticate:

https://accounts.google.com/o/oauth2/v2/auth?client_id=5......

Waiting for your authorization...
Tell us your name to finish creating your account: itdev08

🎉 Welcome to Shorebird, itdev08!
🔑 Credentials are stored in /Users/tmlijktmac08/Library/Application Support/shorebird/credentials.json.
🚪 To logout, use: "shorebird logout".

Your current plan is Hobby.
To upgrade, run shorebird account upgrade.

Please let us know via Discord if we can help!
https://discord.gg/shorebird.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## 

## Log-In

Jika anda sudah melakukan create account maka anda hanya perlu melakukan login dengan menjalankan perintah berikut: 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash
shorebird login
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

jika login berhasil maka akan muncul pesan sebagai berikut:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash
$ shorebird login
The Shorebird CLI needs your authorization to manage apps, releases, and patches
on your behalf.

In a browser, visit this URL to log in:

https://accounts.google.com/o/oauth2/v2/auth...

Waiting for your authorization...

🎉 Welcome to Shorebird! You are now logged in as <email>.

🔑 Credentials are stored in ./path/to/credentials.json.
🚪 To logout use: "shorebird logout".
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

# D. SHOREBIRD TO FLUTTER MODULE

## Basic Shorebird Implementation

Saya asumsikan anda sudah memiliki project flutter yang akan ditambahkan shorebird. Untuk menambahkanya lakukan langkah-langkah berikut: 

1.  Pindah ke direktori project

2.  Jalan kan perintah berikut:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash
shorebird init
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

maka akan tampil pesan berikut:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash
❯ shorebird init                                                                                                                                   
✓ Detecting product flavors (5.9s)
? How should we refer to this app? (shorebird) shorebird

🐦 Shorebird initialized successfully!

✅ A shorebird app has been created.
✅ A "shorebird.yaml" has been created.
✅ The "pubspec.yaml" has been updated to include "shorebird.yaml" as an asset.

Reference the following commands to get started:

🚙 To run your project use: "shorebird run".
📦 To create a new release use: "shorebird release".
🚀 To push an update use: "shorebird patch".

For more information about Shorebird, visit https://shorebird.dev
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1.  Build release app bundle atau apk dengan shorebird dengan perintah sebagai berikut:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash
shorebird release android
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

atau

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash
shorebird release aar
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

note:

-   arr build dan submit archive app android ke shorebird.

-   android build dan submit android app ke shorebird.

Contoh response:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash
❯ shorebird release android --artifact apk                                                                                                                                       
✓ Building release (11.4s)
✓ Fetching apps (0.4s)
✓ Detecting release version (0.2s)
✓ Fetching release (0.3s)

🚀 Ready to create a new release!

📱 App: shorebird (3ed9383b-0d95-4d8d-9b25-c2ce41beff17)
📦 Release Version: 1.2.3+2
🕹️  Platform: android (arm64, arm32, x86_64)

Would you like to continue? (y/N) Yes
✓ Fetching Flutter revision (18ms)
✓ Creating release (0.3s)
✓ Creating artifacts (23.9s)

✅ Published Release!

Your next step is to upload the apk to the Play Store.
build/app/outputs/apk/release/app-release.apk

See the following link for more information:    
https://support.google.com/googleplay/android-developer/answer/9859152?hl=en
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1.  Untuk melakukan update patch, pastikan versi release sama dengan versi yang akan di update patch. Jalankan perintah berikut maka app yang terinstal akan terupdate secara otomatis setelah proses download patch selesai. Perlu diketahui proses download bergantung pada koneksi dan besar update patchnya. Proses download ini terjadi di background jadi kita tidak bisa melihat progressnya. Ketika patch sudah berhasil diunduh. Close app dan buka kembali, maka app sudah terupdate. Untuk submit update patch jalankan perintah berikut:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash
shorebird patch android  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

contoh response:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
bash
❯ shorebird patch android                                                                                                                                                        
✓ Building patch (19.0s)
✓ Fetching apps (0.4s)
✓ Detected release version 1.2.3+2 (0.2s)
✓ Fetching release (0.3s)
✓ Fetching Flutter revision (16ms)
✓ Fetching release artifacts (0.9s)
✓ Fetching aab artifact (0.5s)
✓ Downloading release artifacts (9.1s)
✓ Creating artifacts (3.8s)

🚀 Ready to publish a new patch!

📱 App: shorebird (3ed9383b-0d95-4d8d-9b25-c2ce41beff17)
📦 Release Version: 1.2.3+2
📺 Channel: stable
🕹️  Platform: android [arm64 (49.19 KB), arm32 (49.59 KB), x86_64 (52.77 KB)]

Would you like to continue? (y/N) Yes
✓ Creating patch (0.3s)
✓ Uploading artifacts (3.2s)
✓ Fetching channels (0.3s)
✓ Promoting patch to stable (0.4s)

✅ Published Patch!
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
