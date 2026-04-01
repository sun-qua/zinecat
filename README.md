# ZineCat

**A browser-based MARC 21 record creation tool for zine collections**

ZineCat is a browser-based MARC 21 record creation tool built for the zine collection at the SMFA Library at Tufts University. It is designed to be used by student employees who have little or no formal cataloging training. This tool guides them through the process of original cataloging and creating a MARC 21 bibliographic record that can be imported directly into OCLC Connexion. 

The name ZineCat reflects both its subject focus (zines) and its function as a cataloging assistant. The tool lives as a static HTML file that can be hosted on GitHub Pages or any web server, requiring no backend infrastructure, no login, and no dependencies beyond a modern browser. Our iteration of ZineCat is accessible here: https://sun-qua.github.io/zinecat/.

---

## Background

The W. Van Alan Clark, Jr. Library at the School of the Museum of Fine Arts (SMFA) is a branch of the Tisch Library at Tufts University. The SMFA Library's Zine Collection showcases publications created by the SMFA community and beyond. Founded in 2009, the collection includes a wide range of printing methods, formats, aesthetics, and subject matter. The Metadata Services Department at Tisch Library provides descriptive metadata for the collection.

Zines present particular cataloging challenges in academic and special libraries. They are often self-published, lack standard bibliographic metadata (no ISBN, no publisher information, inconsistent title pages), and are produced in formats that sometimes resist standard physical description norms. At the same time, they are culturally significant primary sources — especially for collections focused on activism, LGBTQIA+ history, feminist movements, and underground art — and deserve the same discoverability in library catalogs as any other format.

Many of the zines we receive in Metadata Services do not have records in OCLC and require original cataloging. Traditionally, student employees have created "brief bib records" in our ILS (Alma) — records with minimal description that fall short of what is needed for full discoverability. A traditional original cataloging workflow would require part-time student employees to understand MARC 21 encoding structure, RDA descriptive standards, Library of Congress Subject Headings (LCSH), and OCLC Connexion — a steep learning curve for any part-time student position.

## What ZineCat does

ZineCat solves this by meeting students where they are:

- **Presents only the fields relevant to zine cataloging**, in plain language with contextual guidance
- **Auto-generates technically complex fixed fields** (LDR, 007, 008, 040, 336/337/338) from the student's input
- **Allowing students to perform subject analysis** with a more user-friendly vocabulary by the Zine Subject Thesaurus
- **Enforces local cataloging conventions** by design (curated relator terms, specific 5XX notes) 
- **Exports a standards-compliant binary MARC 21 file** (`.mrc`) ready for direct import into OCLC Connexion

---

## Usage
Open `index.html` in any modern browser — no installation required. Also hosted on github.io: https://sun-qua.github.io/zinecat/ 

Fill in the form fields from top to bottom. The MARC 21 record preview updates in real time as you type. When the record is complete, use **Export binary .mrc (OCLC)** to download a file ready for import into OCLC Connexion via File > Import Records. A MARCMaker `.mrk` export is also available for use with MARCEdit.

---

## MARC fields covered

| Field | Name | Notes |
|-------|------|-------|
| LDR | Leader | Type a, Blvl m, Elvl 7, Desc i — auto-generated |
| 007 | Physical description fixed field | `ta` (text, unmediated) — auto-generated |
| 008 | Fixed-length data elements | Date, language, country, illustrations, contents — auto-generated from form inputs |
| 020 | ISBN | Optional; most zines lack one |
| 040 | Cataloging source | Fixed: TFW, eng, rda — auto-generated |
| 041 | Language code | Output only for translations or multilingual items |
| 100/110 | Main entry | Personal or corporate name with MARC relator term |
| 245 | Title statement | Title, subtitle, issue/part, statement of responsibility; nonfiling characters auto-calculated |
| 250 | Edition statement | Optional; transcribed as found |
| 264 | Publication info | Handles known dates, copyright-only dates, and unknown dates |
| 300 | Physical description | Extent, illustrations, dimensions |
| 336–338 | Content/media/carrier | RDA fields with `$0` linked data URIs — auto-generated |
| 500 | General note | Physical/production notes, artist website, class project note |
| 504/500 | Bibliography/index note | Auto-generated from checkboxes; 504 for bib refs, 500 for index only |
| 520 | Summary | Free-text description |
| 655 | Genre/form | `Zines. $2 lcgft` always present; additional terms from subject list |
| 6XX | Subject headings | Uses the Zine Subject Thesaurus and an additional field for source unspecified |
| 700/710 | Added entries | Personal and corporate contributors with relator terms |

---

## Local conventions

ZineCat encodes the following SMFA Library / Tisch Metadata Services practices:

- **Organization code** `TFW` 
- **Encoding level 7** (minimal, Srce d) — appropriate for student-created original records pending professional review
- **655 Zines (lcgft)** present on every record
- **500 artist website note** — `Creator's website: [url]`
- **500 class project note** — for zines created as coursework at SMFA at Tufts or Tufts University
- **Curated MARC relator terms** — artist, author, cartographer, colorist, compiler, composer, designer, editor, illustrator, letterer, photographer, printmaker, translator, writer of introduction, writer of preface

---

## Limitations

- Single-item print zines only (monographic, Blvl m)
- Copy cataloging (deriving from or editing an existing OCLC record), as ZineCat is made specifically as an original cataloging tool
- No real-time authority control — name and subject headings must be verified manually against LC authority files
- No holdings, item records, or call number assignment (handled in the ILS after import)
- Does not support non-Latin scripts
- Records are imported one at a time via OCLC Connexion (no batch workflow)
  
---

*Developed by the Metadata Services Department, Tisch Library, Tufts University.*
*SMFA Library Zine Collection founded 2009.*
