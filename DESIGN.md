Purpose and Design
==================

This document concerns why certain design decisions were made and how they relate to LAML's purpose.


Why LAML
--------

LAML is a markup language for documents of legal significance. Its purposes are:

* To encourage modularity and re-use of legal provisions
* To make it easier to detect common legal drafting errors
* To serve as a transition between traditional legal text and machine-executable agreements


LAML is a Markup Language
-------------------------

LAML is primarily intended as a [markup language](http://en.wikipedia.org/wiki/Markup_language), as opposed to a templating language or a representation of data. Although LAML may be used for templating or representation to some extent, there are no shortage of tools better suited to either task, such as [Jinja](http://jinja.pocoo.org/) or [Handlebars](http://handlebarsjs.com/) for templating, [JSON](http://json.org/) or [YAML](http://yaml.org/) for data representation)

As a markup language, LAML allows for the [separation of presentation and content](http://en.wikipedia.org/wiki/Separation_of_presentation_and_content) with respect to aesthetics (or mostly as well as basic HTML does) but *not* necessarily with respect to semantics. Put another way, LAML's understanding of the separation of presentation and content does not necessarily extend to separating content and *data*.

For example, a term may be defined as follows:

    <def>The <name>Investor</name> means Biff Tannen Enterprises.</def>
    
This is not equivalent to `"Investor" === "Biff Tannen Enterprises"`, but rather that any reference to "Investor" should point back to this particular sentence during LAML's error checking.


LAML Does Not Grant Legal Significance
--------------------------------------

As a corollary to being a markup language, while the tags and terms used by LAML may have some particular legal or semantic meaning, the tags do not themselves connote any such meaning. For example, consider the following:

    <def>Make like a <name>Tree</name> and leave.</def>

This statement makes no sense (on multiple levels) yet it remains perfectly valid LAML. Its inclusion in a legal document would not imply the term "Tree" was defined in any way by the above definition, but any subsequent reference in a LAML document would point to this statement.

Similarly, the absence of `<def>` tags does not mean a term that is otherwise defined for the entirety of the document ceases to be defined. The legal significance.

That said, nothing in LAML prevents parties from agreeing to grant legal significance to LAML tags. But in the absence of explicit language to the contrary, parties should not assume LAML tags are a replacement for actual legal language.




