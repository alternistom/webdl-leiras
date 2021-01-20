# webdl-leiras
web-dl módszerek magyarul

- [YOUTUBE-DL WINDOWSON POWERSHELLBEN/COMMAND LINEBAN](#youtube-dl-Windowson-Powershell-vagy-Parancssor-használatával-PATH-nélkül)
- [YOUTUBE-DL WINDOWSON POWERSHELLBEN/COMMAND LINEBAN PATH-EL](#youtube-dl-Windowson-Powershell-vagy-Parancssor-használatával-PATH-el)
- [YOUTUBE-DL ANDROIDON]
- [YOUTUBE-DL LINUXON]
- [STREAM LINK BESZERZÉSE BÖNGÉSZŐBŐL](#Stream-link-beszerzese)
- [YOUTUBE-DL LETÖLTÉSI PARAMÉTEREK](#youtube-dl-letöltési-paraméterek)
- [UTÓMUNKÁLATOK, VÁGÁSOK FFMPEG-EL]
- [HA SEHOGYSE MEGY A YOUTUBE-DL LEHET CHROME KIEGÉSZÍTŐN KERESZTÜL IS](#stream-recorder-használatával)

# youtube-dl Windowson Powershell vagy Parancssor használatával PATH nélkül

(Path telepítése nélkül mindig csak abban a mappában tudunk futtatni, ahol a youtube-dl.exe található, ha szeretnéd bárhonnan futtatni, kattints ide: [YOUTUBE-DL WINDOWSON POWERSHELLBEN/COMMAND LINEBAN PATH-EL](#youtube-dl-Windowson-Powershell-vagy-Parancssor-használatával-PATH-el))

Két programra lesz szükségünk, az egyik a youtube-dl ami letölti a videót illetve az ffmpeg ami pedig összefüzi és kimenti nekünk a streamet. Innen tudjuk letölteni a legfrissebbet:

    https://www.gyan.dev/ffmpeg/builds/ffmpeg-release-full.7z
    https://youtube-dl.org/downloads/latest/youtube-dl.exe
    
1. **youtube-dl és ffmpeg**
    - Készítsünk egy mappát ahonnan a youtube-dl-t fogjuk futtatni, másoljuk ebbe a mappába bele a youtube-dl.exe filet
    - Az ffmpeg-release-full.7z filet csomagoljuk ki, majd a bin mappájából a három darab .exe filet másoljuk át az imént kreált mappába (ffmpeg, ffplay, ffprobe)
    - Nyomjuk le a jobb shiftet és a kattinsunk jobb gombbal a mappában a shiftet lenyomva tartva, amint megnyílt a menü elereszthetjük a Shiftet
    - Válasszuk ki a Powershell-ablak megnyitása itt opciót
    - Kész is a használatra! Következő állomás a [YOUTUBE-DL LETÖLTÉSI PARAMÉTEREK](#youtube-dl-letöltési-paraméterek)
    
2. **Updatelés**
    - Töltsük le megint a két file-t és csomagoljuk/másoljuk át a 4db .exe filet ebbe a mappába

# youtube-dl Windowson Powershell vagy Parancssor használatával PATH-el

Két programra lesz szükségünk, az egyik a youtube-dl ami letölti a videót illetve az ffmpeg ami pedig összefüzi és kimenti nekünk a streamet. Innen tudjuk letölteni a legfrissebbet:

    https://www.gyan.dev/ffmpeg/builds/ffmpeg-release-full.7z
    https://youtube-dl.org/downloads/latest/youtube-dl.exe
   
1. **ffmpeg telepítése**
    - készítsünk egy ffmpeg mappát a merevlemezen valahol, a lényeg hogy legyen egy szeparált rész neki
    - csomagoljuk ki a .7z file tartalmát ebbe a mappába
    
2. **youtube-dl telepítése**
    - készítsünk egy youtube-dl mappát a merevlemezen valahol, a lényeg hogy legyen egy szeparált rész neki
    - másoljuk vagy helyezzük át a letöltött youtube-dl.exe filet ide
    
3. **a két program PATH-ba rakása**
    - erre azért van szükség hogy a két program elérési utját ne kelljen minden alkalommal kiírni
    - Start menűt felnyitva keresünk rá a: __A rendszer környezeti változóinak módosítása__ lehetőségre, majd nyissuk meg
    - A felugró ablakban a Speciális fülén alul van egy környezeti változók... gomb, kattintsunk rá
    - A következő felugró ablak két részre tagolódik, nekünk a felső része fog kelleni
    - Keressük meg a Path nevű változót a táblázatból és kattintsunk rá majd a Szerkesztés... gombra
    - A felugró ablakban a Tallózás... gombra kattintva tudunk felvinni új változót ide
    - A youtube-dl-hez azt a mappát keressük ki ahova az exe filet kimásoltuk, én simán a C: meghajtóra csináltam a mappákat, nálam így néz ki a változó elérési helye:
    
          C:\youtube-dl
    - Az ffmpeg esetében az ffmpeg mappában lévő bin mappába kell betallóznunk, például így:
    
          C:\ffmpeg\bin
    - Majd az OK gombra kattintva zárjuk be a 3 ablakot.
    
4. **Powershell megnyítása**
    - Keressünk rá a Start menüben, vagy egy tetszőleges mappában nyomjuk le a jobb shiftet és a kattinsunk jobb gombbal a mappában a shiftet lenyomva tartva, amint megnyílt a menü elereszthetjük a Shiftet
    - Válasszuk ki a Powershell-ablak megnyitása itt opciót
    - Kész is a használatra! Következő állomás a [YOUTUBE-DL LETÖLTÉSI PARAMÉTEREK](#youtube-dl-letöltési-paraméterek)
    
5. **Updatelés**
    - A két programot úgy tudod frissíteni, hogy letöltöd még egyszer és kicsomagolod/átmásolod az új fileokat a már meglévő mappákba.
    - A youtube-dl frissíthető a következő paranccsal is:
    
          youtube-dl -U

# Stream link beszerzese

Chrome vagy Firefox böngészőben nyissuk meg a videót tartalmazó oldalt, nyomjuk meg az F12-öt ez meg fogja nyitni a Developer Tools-t. Itt át kell váltanunk a Network fülre majd újra betöltenünk az oldalt, majd ezeket végigpróbálni:

1. **.m3u8 link**
    - A Developer Tools bal oldalán lesz egy kis szövegdoboz, ezzel tudunk keresni a találatok között, ide írjuk be hogy m3u8
    - Ha több mint egy találatunk van amik nem egyeznek névre, menjünk a 2-es lépést, ha csak egy találat van kattintsunk rá
    - Majd a felugró ablakból jobb oldalt a Headers fülön lévő Request URL tartalmát másoljuk ki
    
2. **.mpd**
    - Ha nincs egy találat se az m3u8-ra vagy több akkor írjuk be a keresőbe azt hogy: mpd
    - Ha nincs találat menjünk a 3-as lépésre, ha van akkor kattintsunk rá
    - A felugró ablakból a response fülön több m3u8 linjék megtaláljuk, keressük meg a legjobb minőségűt
    
3. **master.json**
    - A Vimeo rendszerét használó streameknél egy harmadik verzió játszik, keressünk rá arra hogy master
    - Az egy találatra kattintsunk rá majd a felugró ablakból a Headers tab-ról a Request URL részt másoljuk ki
    - A link végéről töröljük le a json?base64_init=1 végződést és írjunk m3u8-at a helyére úgy hogy a link vége így nézzen ki: master.m3u8

# Stream Recorder használatával

**Elég lassú és nem túl stabil megoldás, akkor érdemes próbálkozni vele, ha a Youtube-dl-t sehogy se sikerül beüzemelni.**
Ezen módszerhez (jelen állás szerint, ez később változhat) Chrome böngészőre lesz szükségünk.
Nyissuk meg ezt az oldalt:

    https://www.hlsloader.com/index.html

A bővítmény telepítése után nyissuk meg a stream oldalát majd indítsuk el a videót, ezután pedig kattintsunk a kiegészítő ikonjára a jobb felső sarokban. Erre egy új ablak fog felugrani. A Steam Recordernek alapvetően két működési módja van:
- **Normal**
    - Olyan tempóban rögzíti a streamet, amit a helyi hálózat és a kiszolgáló oldal engedi, van hogy lassabban.
- **Record**
    - Valós időben rögzíti a streamet, ha a stream indítása pillanatában nem elérhető az egész videó, akkor nagy eséllyel valós időben megy a stream, ezzel a módszerrel tudjuk felvenni.
    - Annyi ideig fog tartani ameddig a stream maga, vagy amíg valami hálózati galiba miatt esetleg megszakad a kapcsolat, sajnos nem túl stabil. Élő közvetítések rögzítéséhez inkább használjuk valamelyik Youtube-dl-es módszert.

Mindkét módszer végén a SAVE gomb megnyomásával tudjuk elmenteni az mp4 file-t.
