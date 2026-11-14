# bunkerostrom-frissitesek

A Bunkerostrom játék kiadásai. A Windows-indító az `update-manifest.json` alapján frissít,
a böngészős / telefonos változat az `index.html` oldalon keresztül indul.

## Játék iPhone-on (vagy bármilyen böngészőben)

1. A GitHubon: **Settings → Pages → Build and deployment → Deploy from a branch**,
   válaszd ki az ágat és a `/ (root)` mappát, majd **Save**.
2. Egy-két perc múlva a játék elérhető itt: <https://geryxy.github.io/bunkerostrom-frissitesek/>
3. iPhone-on nyisd meg Safariban, és fordítsd fekvőre a telefont.
   Teljes képernyőhöz: **Megosztás → Főképernyőhöz adás**, majd az ikonról indítsd.

Az oldal letölti a `web-manifest.json`-ban megadott `.html.gz` csomagot (kb. 17 MB),
kicsomagolja, és elindítja. iOS 16.4 vagy újabb kell hozzá.

Helyi hálózaton, GitHub Pages nélkül: ebben a mappában `python -m http.server 8000`,
majd a telefonon `http://<a gép IP-címe>:8000/`.

### Érintéses irányítás

| Mit | Hogyan |
| --- | --- |
| Mozgás | bal hüvelykujj a képernyő bal oldalán; teljesen előretolva sprint |
| Nézelődés | húzás a jobb oldalon (a tűzgombon tartva is) |
| Lövés | piros gomb, nyomva tartva sorozat |
| Célzás | `CÉL` gomb (gépkarabély) |
| Ugrás, újratöltés | a tűzgomb melletti gombok |
| Fegyverváltás | koppintás az alsó fegyversávra |
| Bolt, szünet | bal felső gombok |

## Új webes kiadás

Másold be az új `bunkerostrom-game-vX.Y.Z.html.gz` fájlt, és írd át a `web-manifest.json`
`file`, `version` és `bytes` mezőjét. Ha a `web-manifest.json` hiányzik, a weboldal az
`update-manifest.json` kiadását tölti be.

A 2.4.0-s csomag (részletesebb fegyver- és robotmodellek, érintéses irányítás) egyelőre csak a
webes jegyzékben szerepel: az `update-manifest.json` aláírt, ezért a Windows-indítónak szóló
kiadáshoz azt a saját kulccsal kell újra aláírni.
