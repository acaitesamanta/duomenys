Čia pateikiama reikalinga informacija bakalauro darbo ,,Kai kurių NKS duomenų analizės įrankių apžvalga“ praktinės dalies įgyvendinimui.

duomenys.tar.gz išarchyvavimas:
>mkdir duomenys
>cd duomenys
>tar -zxvf ../duomenys.tar.gz

Reikia atsisiųsti VarScan, Pindel, Scalpel įrankius, mutacijoms aptikti.Tai lengviausia padaryti parsisiuntus Miniconda, nes ji padeda lengvai
įdiegti,paleisti ir atnaujinti programas. Jos tampa pasiekiamos iš bet kurios direktorijos.

Miniconda galima parsisiųsti iš https://conda.io/miniconda.html, atsižvelgiant į operacinę sistemą (32 ar 64 bitų) ir Python versiją. Bakalauro
darbe buvo parsisiųsta Miniconda Linux 64 bit Python 2.7. 
Miniconda instaliavimas pateikiamas čia https://conda.io/docs/install/quick.html#.

VarScan galima isntaliuoti komandinėje eilutėje įrašius:
>conda install -c bioconda varscan=2.4.2

Pindel galima isntaliuoti komandinėje eilutėje įrašius:
>conda install -c bioconda pindel=0.2.5b8

Scalpel galima isntaliuoti komandinėje eilutėje įrašius:
>conda install -c bioconda scalpel=0.5.1

Kiti reikalingi įrankiai jau yra aplankale duomenys/.

-----------------------------------------------------------------------------------------------------------------------------------------------

Norint susikurti savo mutacijų atvejį reikia aplankale duomenys/ susikurti naują aplankalą, kuriame ir bus nagrinėjamas mutacijos atvejis, 
pavyzdžiui:
>mkdir 1
>cd 1

Toliau nusikopijuojame bash script'ą generate_all.sh į sukurtą aplankalą 1/
>cp ../generate_all.sh generate_all.sh

Belieka paleisti bash script'ą ir laukti, kol bus sugeneruoti rezultatai, kuriuos pagamins VarScan, Pindel ir Scalpel:
>./generate.sh 50 10000 -i 55555 15 60
50 -- nukleotidų kiekis per eilutę referentinėje sekoje (reference.fa),
10000 -- generuojamas eilučių kiekis referentinės sekos faile (reference.fa),
-i - mutacija, kurią atliksime: -i -- inserciją ar -d -- deleciją,
55555 -- pozicija nuo kurios prasidės mutacija,
15 -- mutacijos ilgis,
60 -- padengimas.
Argumentai gali būti keičiami ir taip kuriami skirtingi atvejai VarScan, Pindel ir Scalpel įrankiams nagrinėti.

Sukurtame faile 1/ atsiras aplankalai varscan/ pindel/ scalpel/, kuriuose bus pateikti atitinkamų programų rezultatai. Toliau galima sukurti
kitą mutacijų atvejį, pavyzdžiui:
>cd ..
>mkdir 2
>cd 2

Ir paleisti generate_all.sh script'ą, kuris sugeneruos kitus rezultatus.

-----------------------------------------------------------------------------------------------------------------------------------------------

Jei turime referentinę (reference.fa), tiriamą sekas (mutated.fa) bei sugeneruotus read'us (mutated1.fq, mutated2.fq) tada tereikia paleisti 
shell script'ą generate_results.sh, prieš tai susikūrus direktoriją (pavyzdžiui, 3/), kurioje bus visi failai, taip pat reikia nusikopijuoti 
script'ą generate_results.sh į šią direktoriją ir jau dabar galime paleisti generate_results.sh script'ą:
>mkdir 3
>cd 3
>cp ../generate_results.sh generate_results.sh
>./generate_results.sh

Script'o rezultatai atrodys taip pat kaip generate_all.sh.

