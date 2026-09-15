# TU Delft Style Report template

Template for a report such as a BSc or MSc thesis following the [TU Delft corporate design](https://www.tudelft.nl/en/tu-delft-corporate-design), using the font family [Roboto Slab](https://fonts.google.com/specimen/Roboto+Slab) and [Arial](https://en.wikipedia.org/wiki/Arial) or alternatively using the LaTeX package '[Fourier](https://ctan.org/pkg/fourier)'.

The template updates the report template by [K. P. Hart](https://www.overleaf.com/latex/templates/tud-report/qrntwbrqpckw).

## Fonts

The fonts can either be:

- Arial (or Roboto) combined with RobotoSlab
  This combination fits the TUD corporate style:
  https://www.tudelft.nl/huisstijl/
- Fourier; a more classic look:
  http://mirrors.ctan.org/fonts/fourier-GUT/doc/fourier-doc-en.pdf

This can be set by either adding or removing the class option `fourier'.

If you use Roboto in LuaLaTeX, you can make use of advanced variable font features

- [Youtube: Amstelvar & Roboto Flex: Unprecedented Flexibility...](https://www.youtube.com/watch?v=K-ruvv6P8sk)
- [Roboto … But Make It Flex](https://m3.material.io/blog/roboto-flex)
- [Exploring typefaces with multiple weights or grades](https://fonts.google.com/knowledge/choosing_type/exploring_typefaces_with_multiple_weights_or_grades)

## Latexmk

`latexmk` is used by Overleaf to determine how the project is to be rendered.
Since we do not want to overrule the compiler set by the user, the line redefining
`pdflatex` is made a comment. An introduction to `latexmk`can be found here:
https://manpages.org/latexmk.

For further inspiration and more features:
- https://www.overleaf.com/learn/how-to/How_does_Overleaf_compile_my_project%3F



## Version management on Gitlab

The source files can be found on [Gitlab](https://gitlab.com/novanext/tudelft-report).
It is designed to work with LuaLaTeX and PdfLaTeX (faster but less features and less fancy font support).
On the Gitlab site more information can be found on using LaTeX and this template outside of Overleaf.

This version was created from Git commit 796d738 on 2026-08-27.


---

# MT44030 -- verslagstructuur

Dit project is opgezet als het verslag voor **MT44030 -- Advanced Mechanics of
Maritime Structures**.

**Auteurs:** Aymen el Moubarik (5597617) en Matthijs Coosen.

## Indeling

Het verslag volgt de opgave een-op-een: het hoofdstuknummer is het
opdrachtnummer en het sectienummer is het vraagnummer. Sectie 3.4 van het
verslag beantwoordt dus vraag 3.4 van de opgave.

| Bestand | Inhoud | Punten |
|---|---|---|
| `cover.tex` | omslag en metadata (titel, auteurs) | |
| `title.tex` | titelpagina met studentnummers, groepsnummer, inleverdatum | |
| `preface.tex` | voorwoord en taakverdeling | |
| `introduction.tex` | inleiding, geometrie, notatie en de lijst met aannames (ongenummerd hoofdstuk) | |
| `assignment1.tex` | Closed Section A | 9 |
| `assignment2.tex` | Open Sections B | 20 |
| `assignment3.tex` | Closed Cells in Sections B | 19 |
| `assignment4.tex` | Idealised Section U -- Analytical vs. ANSYS | 20 |
| `assignment5.tex` | Combined Torsional Analysis | 17 |
| `assignment6.tex` | Scientific Literature | 7 |
| `assignment7.tex` | Structural Monitoring | 8 |
| `appendix.tex` | rekenscripts, Maple-worksheets en ANSYS-bestanden | |

Hoofdstukken 1--3 staan in `\part{Part 1}`, hoofdstukken 4--7 in
`\part{Part 2}`. De volgorde staat in `report.tex`; dat is het enige bestand
dat je hoeft aan te passen als er een hoofdstuk bij komt.

Verder in het project: `figures/` voor alle figuren, `code/` voor de
rekenscripts (die met `\verbatiminput` in de appendix worden opgenomen) en
`report.bib` voor de referenties. In `report.bib` staan nu nog de
voorbeeldreferenties van de template; vervang ze door het artikel van
Assignment 6 en de overige bronnen.

## Hulpcommando's

In de preambule van `report.tex` staan vier commando's die het samenwerken
makkelijker maken:

| Commando | Gebruik |
|---|---|
| `\questionbox{...}` | zet de vraag uit de opgave letterlijk in een kader boven je uitwerking, zodat je altijd ziet wat er precies gevraagd wordt |
| `\tbd{...}` | markeert in het rood wat nog gedaan moet worden |
| `\workedby{...}` | noteert wie een hoofdstuk of paragraaf uitwerkt |
| `\finalanswer{...}` | het eindantwoord van een vraag, kort en expliciet |

**Voor het inleveren:** zoek op `\tbd` en zorg dat er geen enkele meer in het
document staat (`grep -rn 'tbd{' *.tex`). Overleg met de begeleiders of de
vraagkaders (`\questionbox`) in de ingeleverde versie mogen blijven staan; zo
niet, dan kun je het commando in `report.tex` in een keer leeg maken.

## Werkafspraken

- Zet in `introduction.tex` eerst samen de notatie en de lijst met aannames
  vast; daar verwijzen alle hoofdstukken naar (A1, A2, ...).
- Verdeel het werk per hoofdstuk en zet je naam in `\workedby{...}`, dan
  ontstaan er geen merge-conflicten in hetzelfde bestand.
- Elke aanname die je onderweg maakt, voeg je toe aan
  `\ref{sec:assumptions}` in de inleiding.
