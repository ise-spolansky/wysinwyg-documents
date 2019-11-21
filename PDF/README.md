Most people consider PDF to be the "gold standard" for representing documents in a way that will render identically between platforms and mediums --- it's called the *Portable* Document Format for a reason. However, PDF is also a standard that has many, many features that might break this expectation. PDF documents can contain Javascript, 3D models, fillable forms with logic, digital signature metadata, and a host of other information that won't show up in print. Most of those features are primarily supported by Adobe Reader, which will either require the user to [approve](https://helpx.adobe.com/acrobat/using/security-warnings-pdf-opens.html) loading the content or show extra UI elements to alert the user that the document is interactive in some way. 

Instead, we're going to use a little-known PDF feature called [Optional Content Groups](https://help.adobe.com/pdfl_sdk/15/PDFL_SDK_HTMLHelp/PDFL_SDK_HTMLHelp/API_References/PDFL_API_Reference/PD_Layer/PDOCG.html) (OCGs). OCGs are groups of PDF content objects such as text that can be configured to appear or disappear under a number of conditions, including whether or not the PDF is being displayed on a screen or printed. OCGs do not show any UI or warnings, and have wide support across renderers --- the PoC PDF in this repository was tested to render correctly (that is to say, differently in print and on screen) in Adobe Reader, Chrome, and SumatraPDF. 

The easiest way to generate a PDF with OCGs is to use [LaTeX](https://www.latex-project.org) with the [`ocg-p` package](https://ctan.org/pkg/ocg-p?lang=en). By specifying `printocg=never` and setting the initial visibility to `1` (visible), you can insert arbitrary content into the PDF that will not show when printed. Setting `listintoolbar=never` instructs the PDF viewer to not show the OCG in the layers toolbar, which in documents with no other layers usually means no layer UI is shown at all. Inverting the first two options produces content that is invisible on screen and visible when printed. For example:

```latex
\begin{ocg}[printocg=never,listintoolbar=never]{Nonprinting Text}{nonprinting_text}{1}
    This text will appear on screen, but not in print.
\end{ocg}

\begin{ocg}[printocg=always,listintoolbar=never]{Nonprinting Text}{nonprinting_text}{1}
    This text will appear in print, but not on screen.
\end{ocg}
```