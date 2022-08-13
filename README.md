# PDFKit Nodejs
nodejs Express

![Gambar.png]( {Gambar.png} )

## install npm pdfkit
``` html
npm install pdfkit
```

## Require
``` html
const PDFDocument = require('pdfkit');
const fs = require('fs');
```

## Router halaman PDF
``` html
router.get('/',function(req,res,next){

    //.........Paste PDFKit

    //tampilkan halaman berdasarkan posisi file;
    res.render('users',{
        title:'Download PDF',
        link:'belum'
    });
});
```

## PDF Kit
``` html
    //tanggal otomatis hari ini;
    var tgl=new Date();
    var hr=tgl.getDate();
    var bln=tgl.getMonth()+1;
    var thn=tgl.getFullYear();

    // Membuat File PDF Baru, dan ukuran kertas;
    const doc = new PDFDocument({ size: "A4", margin: 50 });

    //lokasi menyimpan file;
    doc.pipe(fs.createWriteStream('output.pdf'));

    //kop atas
    doc
    .image("./public/images/logoku.png", 50, 45, { width: 50 })
    .fillColor("#444444")
    .fontSize(20)
    .text("Jasaku Media Tech", 110, 57)
    .fontSize(12)
    .text("Website, Mobile, Desktop, IoT", 110, 77)
    .fontSize(10)
    .text("Jasa IT Konsultan", 200, 50, { align: "right" })
    .text("Jl. Barau barau No.16, Jambi, Jambi Selatan", 200, 65, { align: "right" })
    .text("Jambi, "+hr+"/"+bln+"/"+thn+".", 200, 80, { align: "right" })
    .moveDown();

    //============================================================================
    //kop tengah
    doc
    .fillColor("#444444")
    .fontSize(20)
    .text("Invoice", 50, 160);

    //data diri pembeli
    const customerInformationTop = 200;
    doc
    .fontSize(10)
    .text("Invoice Number:", 50, customerInformationTop)
    .font("Helvetica-Bold")
    .text("1234", 150, customerInformationTop)
    .font("Helvetica")
    .text("Invoice Date:", 50, customerInformationTop + 15)
    .text(""+hr+"/"+bln+"/"+thn, 150, customerInformationTop + 15)
    .text("Balance Due:", 50, customerInformationTop + 30)
    .text("Rp 100.000", 150, customerInformationTop + 30)

    .font("Helvetica-Bold")
    .text("Wahyu Illahi", 300, customerInformationTop)
    .font("Helvetica")
    .text("082244666681", 300, customerInformationTop + 15)
    .text("Kota Lubuklinggau, Sumsel, ID", 300, customerInformationTop + 30)
    .moveDown();

    //========================================================================
    const customerInformationTop2 = 280;
    doc
    .fontSize(10)
    .font("Helvetica-Bold")
    .text("Kode Barang", 50, customerInformationTop2)
    .text("Nama Barang", 160, customerInformationTop2)
    .text("Banyak", 280, customerInformationTop2)
    .text("Harga", 350, customerInformationTop2)
    .text("Total", 450, customerInformationTop2)
    .moveDown();


    const customerInformationTop3 = 300;
    var data=5;//banyak data;
    var top=0;//jarak top;
    var no=0
    //menampilkan data sesuai banyaknya data;
    for(var i=0;i<data;i++){
        top=top+15;//jarak top;
        no=no+1;
        doc
        .fontSize(10)
        .font("Helvetica")
        .text("00"+no, 50, customerInformationTop3+top)
        .text("Hardisk 500Gb", 160, customerInformationTop3+top)
        .text("2 Unit", 280, customerInformationTop3+top)
        .text("Rp 1800000", 350, customerInformationTop3+top)
        .text("Rp 1600000", 450, customerInformationTop3+top)
        .moveDown();
    }

    //total, turun otomatis sesuai banyaknya data;
    doc
    .fontSize(10)
    .font("Helvetica-Bold")
    .text("Total Belanja", 350, customerInformationTop3+top+20)
    .text("Rp 160000000", 450, customerInformationTop3+top+20)

    .font("Helvetica")
    .text("PPN 15%", 350, customerInformationTop3+top+35)
    .text("Rp 1000", 450, customerInformationTop3+top+35)

    .text("Tagihan", 350, customerInformationTop3+top+50)
    .text("Rp 200000000", 450, customerInformationTop3+top+50)
    .moveDown();



    // Finalize PDF file
    doc.end();
```

# Support
Follow my instagram : https://www.instagram.com/wahyu_illahi07/ 
Youtube Channel : https://www.youtube.com/playlist?list=PL2DC6n3PrEKVXN9nvzONe9idXa9BgCusj
