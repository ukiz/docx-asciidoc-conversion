# docx-asciidoc-conversion



#### Prerequisites

- [Pandoc](https://pandoc.org/), version 2.14.0.3 used
- Python, version 3.8.3 used

#### Usage

1. Correct the original docx document, save as `md_2_fixed.docx`:
   - apply *XML Example* style to all XML examples (several cases)
   - remove paragraph breaks from inside footnotes (one case)

2. Convert the corrected docx document to Asciidoc using Pandoc, save as `md_2_pandoc.adoc`:
    ```shell
    pandoc md_2_fixed.docx -f docx -t asciidoc -o md_2_pandoc.adoc --wrap=none --extract-media=. --markdown-headings=atx
    ```
    
1. Convert the corrected docx document to markdown including additional styles information, save as `md_2_styles.md`:
    ```shell
    pandoc md_2_fixed.docx -f docx+styles -t markdown -o md_2_styles.md --wrap=none --markdown-headings=atx
    ```
    
4. Run Python script with arguments: adoc from 2., md from 3. and Asciidoc attributes file, it will create `md_2_final.adoc` file:
    ```shell
    python post_pandoc.py md_2_pandoc.adoc md_2_styles.md attributes.adoc
    ```


#### Files

`md_2_0_1.docx` original docx MS Word, Metadata Technical Guidance 2.0 document

`md_2_fixed.docx` corrected docx MS Word, Metadata Technical Guidance 2.0 document

`md_2_final.adoc` final Asciidoc , Metadata Technical Guidance 2.0 document

`attributes.adoc` attributes to include in the Asciidoc document

`post_pandoc.py` Python script

