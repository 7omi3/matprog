# N-test Szimuláció Barnes–Hut (2D)

Ez a szkript n részecske gravitációs kölcsönhatását modellezi a Barnes–Hut algoritmus segítségével 2D térben. A program minden lépésben PNG képkockát ment, amelyekből videó készíthető.

# Követelmények

* Python >= 3.9
* numpy
* matplotlib
* scipy

# Telepítés
cmd
pip install numpy matplotlib scipy


# Futtatás
cmd
python nbody_simulation.py


Indítsd a parancsot cmd-ből (vagy csak egyszerűen notebook-ból). A szkript első futáskor létrehozza (ha létezik, újra létrehozza) a nbody_szimulacio_kimenet mappát, ide menti a képkockákat frame_00000.png, frame_00001.png, … néven.

A paraméterek (részecskeszám, lépésszám, időlépték, stb.) a fájl elején globális változóként találhatók, szabadon módosíthatók.

# Kimenet

1. A futás végén minden képkocka a nbody_szimulacio_kimenet könyvtárban lesz.
2. A terminálban megjelenik a teljes futási idő.

Ha szeretnéd animációvá alakítani a képkockákat (30 fps):

cmd
ffmpeg -framerate 30 -i nbody_szimulacio_kimenet/frame_%05d.png -c:v libx264 -pix_fmt yuv420p simulation.mp4


# Mit csinál a program?

1. Inicializáció – n részecske kezdeti pozícióját és sebességét véletlenszerű, korong‑alakú eloszlásból generálja
2. QuadTree építés – minden időlépésben felépíti a Barnes–Hut quad‑fát az aktuális pozíciókkal
3. Erőszámítás – a fa segítségével közelítőleg, theta=0,7 nyitási szöggel számolja a gravitációs erőket
4. Integrálás – egyszerű sémával frissíti a sebességeket és pozíciókat
5. Vizualizáció – minden lépésben képkockát rajzol, ahol a pontok színe a helyi részecske‑sűrűségtől függ

A sötét háttér és a sűrűségfüggő színezés segít kiemelni a kialakuló struktúrákat, például spirálkarokat vagy sűrűbb magokat.

Ezen kóddal készített videó:  https://youtube.com/shorts/-CbYYQ1g2WE
Másik kóddal készített videó: https://www.youtube.com/watch?v=tPBjRBRBv8k
