This repository contains examples of "misprinting" documents. That is, documents that misuse legitimate features in their format or bugs in standard renderers to appear signficantly differently on screen than in print. Such documents could be used to scam a user who for example reads a contract on their screen, then prints it out and signs it --- they could be signing a very different document than they believe they were. 

The rise of desktop publishing was built on the concept of WYSIWYG (What You See Is What You Get) document editing, where a document is drawn on screen as close to identically to how it will appear in print as possible. This document editing paradigm has become so ingrained in how people interact with desktop publishing software such as Microsoft Word or Adobe Reader that most users do not do more than a perfunctory comparison between any printed documents and what they reviewed on their screen. Meanwhile, many document editors and formats have extremely advanced capabilities that allow them to produce interactive or semi-interactive content, or content that responds to different screen sizes or mediums. These features are usually benign in a vacuum, but like any other interesting software feature can be misused to harm users. 

The documents contained in this repository are all designed to appear like contracts or other official documents, and abuse various format features to appear different on screen than in print. Each folder contains:

- a README desribing the document format, the technique or feature used to create the "misprint"
- the document itself
- any source code or source markup (e.g. LaTeX for PDFs)
- a PDF and/or PNG screenshots showing the difference between the document as displayed and as printed. Showing the documents as printed is accomplished by using a print to PDF printer.
