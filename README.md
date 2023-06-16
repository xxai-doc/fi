<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

On suositeltavaa asentaa ensin nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) ja sitten `direnv allow` hakemistoon siirtymisen jälkeen ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) suoritetaan automaattisesti hakemistoon siirtymisen jälkeen).

Merkitys on: kiinalainen käännös japaniksi, koreaksi, englanniksi, englanninkielinen käännös kaikille muille kielille. Jos haluat tukea vain kiinaa ja englantia, voit kirjoittaa vain `zh: en` .

Merkitys on: kiinalainen käännös japaniksi, koreaksi, englanniksi, englanninkielinen käännös kaikille muille kielille. Jos haluat tukea vain kiinaa ja englantia, voit kirjoittaa vain `zh: en` .

* [käyttöliittymäkoodi](https://github.com/xxai-art/web)
* [Kielipaketit koko sivustolle](https://github.com/xxai-art/web/tree/main/i18n)
* [Kielipaketit kirjautumismoduuleille](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Verkkosivuston monikielinen dokumentaatio](https://github.com/xxai-doc)

Käyttöliittymän ohjelmointikieli on [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , joka lisää joitain ominaisuuksia coffeescript-syntaksiin, katso [./coffee_plus.md](./coffee_plus.md) .

## Verkkosivujen ja asiakirjojen kansainvälistäminen

Rakenna seuraavien 3 projektiin

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Suffiksi on `.mdt` , voit käyttää syntaksia, joka on samanlainen kuin `<+ ./coffee_plus/import.js>` viitataksesi ulkoisiin tiedostoihin ja luoda merkintöjä jälkiliitteellä `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Markdown-käännös ei käännä koodeja ja linkkejä, vaan tallentaa käännetyt lauseet välimuistiin. Jos käännöstä muutetaan, mutta alkuperäistä tekstiä ei ole muokattu, sen uudelleen suorittaminen ei korvaa käännöksen muutosta.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Kielitiedostot `yaml` luomien verkkosivustojen kääntämiseen.

### Asiakirjojen käännösautomaation ohjeet

Katso koodivarasto [xxai-art/doc](https://github.com/xxai-art/doc)

On suositeltavaa asentaa ensin nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) ja sitten `direnv allow` hakemistoon siirtymisen jälkeen ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) suoritetaan automaattisesti hakemistoon siirtymisen jälkeen).

Välttääkseni suuren koodikannan kääntämisen sadoille kielille, loin jokaiselle kielelle erillisen koodikannan ja loin organisaation koodikannan tallentamiseksi.

Asettamalla ympäristömuuttujan `GITHUB_ACCESS_TOKEN` ja suorittamalla sen jälkeen [create.github.coffee,](https://github.com/xxai-art/doc/blob/main/create.github.coffee) koodivarasto luodaan automaattisesti.

Voit tietysti laittaa sen myös koodipohjaan.

Käännösskriptin viite [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Skriptikoodi tulkitaan seuraavasti:

[bunx](https://bun.sh/docs/cli/bunx) korvaa npx:n, joka on nopeampi. Tietenkin, jos sinulla ei ole buna asennettuna, voit käyttää sen sijaan `npx` ää.

`bunx mdt zh` tekee `.mdt` n zh-hakemistossa muodossa `.md` , katso 2 linkitettyä tiedostoa alla

* [coffee_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` on käännösten ydinkoodi (jos sinulla on vain `nodejs` asennettuna, mutta `bun` ja `direnv` eivät ole asennettuina, voit myös kääntää `npx i18n` ).

Se jäsentää [tiedoston i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , tämän asiakirjan `i18n.yml` kokoonpano on seuraava:

```
en:
zh: ja ko en
```

Merkitys on: kiinalainen käännös japaniksi, koreaksi, englanniksi, englanninkielinen käännös kaikille muille kielille. Jos haluat tukea vain kiinaa ja englantia, voit kirjoittaa vain `zh: en` .

Viimeinen on [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , joka poimii sisällön kunkin kielen `README.md` pääotsikon ja ensimmäisen alaotsikon väliltä ja luo merkinnän `README.md` . Koodi on hyvin yksinkertainen, voit katsoa sen itse.

Google-sovellusliittymää käytetään ilmaiseen käännökseen. Jos et voi käyttää Googlea, määritä ja aseta välityspalvelin, kuten:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Käännösskripti luo käännetyn välimuistin `.i18n` -hakemistoon. Tarkista se `git status` ja lisää se koodivarastoon toistuvien käännösten välttämiseksi.

Päivitä välimuisti suorittamalla `bunx i18n` aina, kun muokkaat käännöstä.

Jos alkuperäistä tekstiä ja käännöstä muokataan samanaikaisesti, välimuisti menee sekaisin, joten jos haluat muokata, voit muokata vain yhtä ja päivittää välimuistin suorittamalla `bunx i18n` .
