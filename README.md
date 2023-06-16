<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

Osa verkkosivuston koodista on avointa lähdekoodia, tervetuloa auttamaan käännöksen optimoinnissa.

## käyttöliittymäkoodi

* [käyttöliittymäkoodi](https://github.com/xxai-art/web)
* [Kielipaketit koko sivustolle](https://github.com/xxai-art/web/tree/main/i18n)
* [Kielipaketit kirjautumismoduuleille](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Verkkosivuston monikielinen dokumentaatio](https://github.com/xxai-doc)

Käyttöliittymän ohjelmointikieli on [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , joka lisää joitain ominaisuuksia coffeescript-syntaksiin, katso [./coffee_plus.md](./coffee_plus.md) .

## Verkkosivujen ja asiakirjojen kansainvälistäminen

Rakenna seuraavien 3 projektiin

### [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

Merkintämalli, jossa on pääte `.mdt` , voi viitata ulkoisiin tiedostoihin, joiden syntaksi on samanlainen kuin `<+ ./coffee_plus/import.js>` .

[@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

Markdown-käännös ei käännä koodeja ja linkkejä, vaan tallentaa käännetyt lauseet välimuistiin. Jos käännöstä muutetaan, mutta alkuperäistä tekstiä ei ole muokattu, sen uudelleen suorittaminen ei korvaa käännöksen muutosta.

[@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

Kielitiedostot `yaml` luomien verkkosivustojen kääntämiseen.
