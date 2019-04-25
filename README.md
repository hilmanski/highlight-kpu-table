Untuk yang lagi mengawasi website resmi pemilu2019 
bisa melihat secara visual pasangan mana yang menang per daerah

Caranya:
1. Klik kanan 
2. Pilih Inspect
3. Tab console
4. Paste kode dibawah
```
var allRows = document.getElementsByTagName("tr")    
for(var i=0; i<allRows.length; i++) { 
    cell = allRows[i].cells
    if(parseInt(cell[1].innerHTML.replace(/\./g, "")) > parseInt(cell[2].innerHTML.replace(/\./g, ""))) {
        cell[1].style.backgroundColor = "#0766A9"
        cell[1].style.color = "white"
    } else  {    
        cell[2].style.backgroundColor = "#0766A9"
        cell[2].style.color = "white"
    }    
}
```

Pasangan yang menang akan terhighlight warna biru
