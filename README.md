Untuk yang lagi mengawasi website resmi pemilu2019 
bisa melihat secara visual pasangan mana yang menang per daerah

[Update] menampilkan data kemenangan per daerah di atas table

Caranya, buka website https://pemilu2019.kpu.go.id/#/ppwp/hitung-suara/:
1. Klik kanan 
2. Pilih Inspect
3. Tab console
4. Paste kode dibawah, di bawah tab consolenya
```
for(var allRows=document.getElementsByTagName("tr"),paslon1=[],paslon2=[],i=1;i<allRows.length;i++)cell=allRows[i].cells,parseInt(cell[1].innerHTML.replace(/\./g,""))>parseInt(cell[2].innerHTML.replace(/\./g,""))?(highlightCell(cell[1]),paslon1.push(cell[0].firstChild.innerHTML)):(highlightCell(cell[2]),paslon2.push(cell[0].firstChild.innerHTML));function highlightCell(e){e.style.backgroundColor="#0766A9",e.style.color="white"}function showList(e,l){var n=document.createElement("P"),a=document.createTextNode(e+" menang di "+l.length+" daerah -> "+l.join(","));n.appendChild(a);var t=document.getElementsByClassName("data-table")[0];t.insertBefore(n,t.childNodes[0])}showList("Prabowo-Sandi : ",paslon2),showList("Jokowi-Ma'ruf : ",paslon1);
```

Pasangan yang menang akan terhighlight warna biru (Per daerahnya, bukan nama)

Contoh gambar

![contoh screenshot](https://i.ibb.co/cDyypbz/Screen-Shot-2019-04-25-at-10-24-35-PM.png)

Buat yang mau ngelihat kodenya (versi mudah dibaca)
```
var allRows = document.getElementsByTagName("tr")    
var paslon1 = [], paslon2 = []
for(var i=1; i<allRows.length; i++) { 
    cell = allRows[i].cells
    if(parseInt(cell[1].innerHTML.replace(/\./g, "")) > parseInt(cell[2].innerHTML.replace(/\./g, ""))) {
        highlightCell(cell[1])
        paslon1.push(cell[0].firstChild.innerHTML)
    } else {
        highlightCell(cell[2])
        paslon2.push(cell[0].firstChild.innerHTML)
    }    
}

function highlightCell(cell) {
    cell.style.backgroundColor = "#0766A9"
    cell.style.color = "white"
}

showList("Prabowo-Sandi : ", paslon2)
showList("Jokowi-Ma'ruf : ", paslon1)

function showList(names, list) {
    var newItem  = document.createElement("P");
    var textnode = document.createTextNode(names + " menang di " + list.length + " daerah -> " + list.join(","));
    newItem.appendChild(textnode); 

    var table = document.getElementsByClassName('data-table')[0]
    table.insertBefore(newItem, table.childNodes[0])
}
```
