# STREAMS

_Tak teď už by jste měli být schopni vydělávat dobře a prodělávat 
minimálně, i s jednou rukou za zády a jedním okem zavázaným. 
Jednodušeji už to nejde._

_Vězte, že je to čerstvé, takže může dojít k maličkým úpravám v 
nastavení, ale vymodelované by to mělo být dobře. Nicméně body 7, 8, 9 
a 10 budu ještě několik dnů sledovat, aby jsem viděl jak se budou 
chovat v reálu, tekže zatím neochodovat, ale myslím že jsme na vrcholu 
obecných analýz. Dál už to bude otázka detailních analýz a ty se 
publikovat nedají, nechce-li člověk vytvářet pumpy._

_Jako vždy, pro zobrazení budete v Chromiu potřebovat jsonview plugin 
anebo použijte firefox. Jsony se automaticky neaktualizují, takže 
nezapomeňte refreshnout._

_Připomínám znova a znova, tohle NENÍ systém kup, prodej, lambo, pokud
takový systém očekáváte, radši se těmito streamy vůbec neřiďte a obraťte
se někam jinam, úplně ignorujte, že tyto streamy existují. Cílem systému
je Vám poskytnout kontext trhu a odfiltrovat Vám spoustu smetí a nechat 
Vás se soustředit na Vaší vlastní strategii u předfiltrovaných párů._

---

**1.   Zkontrolujte stav trhu, aby vyhovoval Vaší strategii. (Aka na trhu jehož MH je 0.5 si nechcete otevřít 7 long pozic)**

**2. Vyberte si páry ze skupiny, která odpovídá Vaší strategii.**

**3. Páry si zkontrolujte na grafu (např.supporty, resistence) a zjistěte zda výběr odpovídá Vaší strategii.**

---

## JSON struktura

    1. Název aplikace.
    2. Čas.
    3. Trend USD-BTC.
    4. Market Healths
    5. Uptrendy
    6. Downtrendy
    7. Trend changes DOWN > UP.
    8. Trend changes UP > DOWN.
    9. Undervalued for last 48 hours.
    10. Undervalued for last 48 hours + uptrend change.


## Popis:
    1. Název.

    2. Čas vždy zkontrolovat, data nesmí být starší než 60 minut.

    3. Uptrend, Downtrend, Strength pro USD-BTC. Uptrend a downtrend offset je 3.0 Strength offset je 2.5

    4. Posledních 24 hodnot Market Health seřazených od nejaktuálnějšího po nejstarší. Market Health je ukazatelem trendu celého ALT trhu. Seřazení za posledních 24 hodin, od nejaktuálnějšího k nejstaršímu.
    
        0 - 1.0
        Znamená hodně špatnou kondici, kdy je dobrý veškeré ALTy, kromě opravdu silných uptrendů, prodat a přejít do BTC. Pokud se k tomu připojí i klesání BTC, rozhodně bych kompletně přešel do fiatu. Zejména pokud předcházely hodnoty MH vyšší, než 1.0. 1.0 je dokonale vyvážený a pokud se kolem této hodnoty pohybujeme dlouhodobě, znamená mrtvý trh. 
        
        1.0 - 1.4
        Znamená stále nestabilní kondici, tam je třeba také si dávat pozor. Speciálně pokud byl stav trhu v předchozím období dobrý (klesání). Pokud předcházelo vyklesání trhu můžou se zde objevovat zajímavé příležitosti, předcházel-li rychlý růst MH.Pokud jsme se dlouhodobě pohybovali pod 1.0, nárůst MH a překročení 1.0, může být dobrý bod pro otevření pozic, je-li nárůst MH dostatečně rychlý a silný.
        
        1.4 a více
        Je dobrá kondice, nad 2.0 už máme silný uptrend celého trhu.
        
        
            Kombinace MH a BTC trendu pro predikci BTC:
            
            MH up + BTC up		-> BTC stabilní, držet.
            MH down + BTC up	-> BTC up, držet.
            MH up + BTC down	-> jen korekce BTC, držet.
            MH down + BTC down	-> Zlom trhu a BTC, přejít do FIATu.

            Obecně je dobré sledovat také dlouhodobé průměry MH, jeho supporty,
            resistence atd.
            
            MH je mladý indikátor (cca 9 měsíců) vyvinutý primárně, jako interpretačně jednoduchý číselný mechanismus, který měl zabránit AOSům prodělávat na medvědím trhu, funguje stejně i pro tradery.
            
            Vzoreček se časem proměnil a vstupní data jsou preprocesována některými indikátory, hlazena atd., takže dávají sensitivnější data, občas až moc sensitivní a pokud se stane v MH ukazateli nějaký extrém, můžete si být jisti, že to něco znamená. Minimálně bývá o 2 cndls napřed, tak s tím počítejte.
            
            Pokud nevíte co je s trhem, kdy a zda vůbec, do něj vstoupit, chcete li se vyhnout ztrátám, způsobeným obchodováním na trhu, který už je dávno medvědí, anebo stále medvědí, MH se Vám bude určitě hodit. Může odfiltrovat ta největší nebezpečí. Zároveň i další ukazatele ve skupině jsou relevantnější v závislosti na MH. Je už jen statisticky spolehlivější, vyhledávat změny trendů, při změně trendu celého trhu atd. Navíc se od něj výborně predikuje vývoj kurzu BTC.
            
            MH pozorujte a vězte, že často ukazuje věci, které na trhu ještě
            třeba dva dny nebude vidět.

    5. Trusted
        
        V Trusted jsou uptrendy skupiny cca 65% ALTů s největší kapitalizací za posledních 24 hodin.
        
            Pro každý pár ve skupině máme 3 další parametry:
                
                Uptrend health - 0.0 - 100.0, offset je 10.0. Značí vnitřní kondici trendu. Odečítá rušivé vlivy atd.
                Strength - 0.0 - 10.0, offset 2.5. Síla trendu.
                Uptrend - 0.0 - 10.0, offset 3.0 Síla Uptrendu.

        Untrusted
            
            To samé jako v Trusted jen pro zbývajících 35% ALTů.
             Tady samozřejmě zaleží na stavu trhu. Pokud je celý trh dlouhodobě slabý, je to jiná situace, než když máme pěkný silný trh, tak opět, berte to celé v rámci kontextu.

    6. Platí to samé jako u Uptrendů, jen pro Downtrendy.

    7. Změny trendu z DOWN v UP:
        
        Zde mějte na paměti, že není možné zachytit všechny změny a filtr je nastaven tak, aby zachycoval již silně trendující páry. Tj. páry které mají vysokou hybnost trendu, tj. silně padaly a teď se obrací a ne ty které se do pohybu teprve dostávají. Také pochopitelně, ne všechny zachycené změny se musí potvrdit. Zde proveďte dvojitou kotrolu toho, zda všechny Vaše podmínky odpovídají, stejně jako aplikaci vlastního pohledu na věc a vlastní strategie. Tyto filtry Vám podávají komplexní přehled trhu, tak, aby jste si mohli jen vybírat nejpříhodnější páry pro Vaše obchody, ale mají určité omezení ve standardizaci. Samozřejmě zase zpětně, nejlépe se pozice otevírají, když nám i MH ukazuje že se trend celého trhu láme z medvědího na býčí. Nicméně na výběr je z mnoha párů, takže příležitosti jsou takřka neomezené a výběr, spolu s kontrolou grafů a kontextu, se mi ukázal fungovat téměř neomylně. Pokud chcete ještě větší jistotu, pak se v k tomu příhodných obdobích, koukejte na bod 10.

    8. Změny trendu z UP v DOWN:
       
        To samé jako 7, jen obráceně. Tentokrát, jsou však srovnány dle výše svého DOWN trendu, což znamená, že hledáte li páry na LONG, hledejte na konci skupiny, pro páry, které by se brzy mohli otočit, o to větší péči potom musíte dát samozřejmě kontrole svých strategiií a pravidel.

    9. V této sekci jsou všechny páry jež se nacházejí pod svým 48h průměrem.
    
        Zde nám přibyl jeden ukazatel '%under48hAVG', jež nám ukazuje počet procent pod tím 48h průměrem. Všimněte si že páry jsou srovnané dle  velikosti svého uptrendu, takže si můžete, po zkontrolování downtrendu, strength a %under48hAVG, poměrně snadno vybírat páry které jsou nejlepší na zobchodování. Nejsilnější uptrendy, pokud jsou přítomny, jsou na začátku. Opět podrobujte poctivě svému vlastnímu pohledu na situaci a kontext.

    10. Zde máme všechny páry, jež jsou pod svým 48h průměrem a jejichž trend se mění z DOWN v UP trend.
        
        Z logiky této skupiny vyplývá, že po většinu času, zde nebude mnoho párů, často žádný. Protože pokud jde celý trh dolů, či je již nahoře, do této skupiny se páry nedostanou. Dostávají se sem, narozdíl od předchozí skupiny, hromadně, když se trh láme z medvědího v býčí, ve svých kratších intervalech. Opět závisí na stavu MH, jak relevantní ukazetel bude.

---

## Obecný postup
První kontrolujete MH a trend BTC, aby jste se přesvědčili, zda máte 
Vámi chtěné podmínky. Po té si ze skupin ukazatelů ve streamech 
vybíráte páry s parametry, které odpovídají Vaši obchodní strategii. 
Pak to zkontolujete podle své strategie na grafech. Supporty, resistence 
atd. Všechny tři postupy jsou stejně důležité.

Jestliže jsou některé ukazatele natolik přesné že se to dá občas 
zobchodovat i pod svým bezpečným limitem, vězte že to děláte na vlastní 
nebezpečí.

Pamatujte, že nedržíte v rukách stand-alone, instantní návod na nákupy a
prodeje, ale nástroj, který pokud se jej naučíte, může výrazně zlepšit a
zvýšit Vaše výdělky a zároveň Vám nabíddnout velice rychlý, pohled na kontext 
trhu, aby jste o své výdělky nepřišli neuváženým obchodováním na trhu, na
kterém se aktuálně vydělat již nedá, pokud se nám trh hroutí.

Ještě jedno malé soukromé doporučení pro ty výběrové skupiny, pokud Vám 
komplexní situace trhu poukazuje na to, že je trh ve špatném stavu, 
nesnažte se za každou cenu, dokud si nejste absolutně jisti tím co 
děláte, udělat obchod, ale dejte si pauzu. A pokud nejste schopni 
vyčíst z ukazatelů, jak na tom trh je, pár hodin počkejte, trh se sám 
vyjasní, má prostě své slepé období, kdy ani trh sám neví kam půjde.


## Vysvětlivky
_(Všechny hodnoty jsou popisnými hodnotami, ne filtry symotnými!)_

- Uptrend:		Síla uptrendu 0.0 - 10.0.
- Downtrend:		Síla downtrendu 0.0 - 10.0.
- Strength:		Síla trendu 0.0 - 10.0.
- %under48hAVG:		Počet procent, které je aktuální cena pod svým 48h průměrem.
- TRUSTED:		70% párů BTC, s největší marketcap za 24 hodin.
- UNTRUSTED:		Zbylé páry BTC. 


# https://api.myjson.com/bins/1dk2ol
