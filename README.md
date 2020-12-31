# webdl-leiras
web-dl módszerek magyarul

- [YOUTUBE-DL WINDOWSON POWERSHELLBEN/COMMAND LINEBAN](#youtube-dl-Windowson-Powershell-vagy-Parancssor-használatával)
- [YOUTUBE-DL WINDOWSON UBUNTU TERMINÁLLAL]
- [YOUTUBE-DL ANDROIDON]
- [YOUTUBE-DL LINUXON]
- [STREAM LINK BESZERZÉSE BÖNGÉSZŐBŐL](#stream-link-beszerzese)
- [YOUTUBE-DL LETÖLTÉSI PARAMÉTEREK]
- [UTÓMUNKÁLATOK, VÁGÁSOK FFMPEG-EL]ű
- [HA SEHOGYSE MEGY A YOUTUBE-DL LEHET CHROME KIEGÉSZÍTŐN KERESZTÜL IS](#stream-recorder-használatával)

# youtube-dl Windowson Powershell vagy Parancssor használatával 

Két programra lesz szükségünk, az egyik a youtube-dl ami letölti a videót illetve az ffmpeg ami pedig összefüzi és kimenti nekünk a streamet.

    https://www.gyan.dev/ffmpeg/builds/ffmpeg-release-full.7z
    https://youtube-dl.org/downloads/latest/youtube-dl.exe
   
- ffmpeg telepítése
- youtube-dl telepítése

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
