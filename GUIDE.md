Guide
=====

LAML does not require any particular file extension, but we recommend using .xml files to make it easier for editors to auto-detect. All LAML should be valid, well-formed XML.

Documents
---------

A document is the basic unit of agreement. It is designated with a `<doc>` tag. You can define multiple documents in a LAML file, although it may be easier to organize if you give each document its own file. Below is an example of a simple legal agreement, represented in LAML.

```xml
<doc namespace="https://docbrownenterprises.com" id="sales-123">
  <!-- Human-readable name for this agreement -->
  <name>Time Machine Sales Agreement</name>
  <body>
    <!-- Sections are the basic building blocks of a doc. Each section
    must have an id or a name for identification purposes. The id or
    name should be unique within the doc. -->
    <section id="intro"><p>
      This <def>Time Machine Sales Agreement (the <name>Agreement</name>)</def>
      between
      <def>Doc Brown Enterprises, Inc. (the <name>Company</name>)</def>
      and
      <def>McFly Nuclear Corp. (the <name>Purchaser</name>)</def>
      is made as of <data type="date" format="YYYY-MM-DD">2015-10-21</data>
    </p></section>
    
    <!-- Note that section does not need an id because it has a name
    element. -->
    <section><p>
      <name>Sale</name>. The <ref to="Company" /> hereby agrees to sell
      <def>one Flux Capacitor (the <name>Goods</name>)</def> to the
      <ref to="Purchaser" />. Title shall pass to the <ref to="Purchaser" />
      at such time as full payment is received by the <ref to="Company" />
      pursuant to <ref to="Payment" />.
    </p></section>
    
    <section><p>
      <name>Price</name>. The <ref to="Purchaser" /> agrees to purchase the
      <ref to="Goods" /> for the agreed upon price of
      <def>
        <data id="price-number" type="number">12,100,000,000</data>
        dollars (the <name>Price</name>)
      </def>,
      and shall also pay any applicable sales or transfer taxes.
    </p></section>
    
    <section><p>
      <name>Payment</name>.
      Full payment of the <ref to="Price" /> shall be made in full upon signing
      of this <ref to="Agreement" />.
    </p></section>
    
    <!-- This includes the body of a boilerplate module -->
    <include module="boilerplate" />
  </body>
  
  <!-- Information about who should sign this document -->
  <signatories>
    <signatory>
      <name><ref to="Company" /></name>
      <signatory>
        <!-- Nested signatory tags indicate that one signatory is signing on
        behalf of another signatory. In this case, Doctor Emmett Brown is
        signing for the Company. -->
        <name>Doctor Emmett Brown</name>
        <!-- The role tag describes in what capacity Doctor Emett Brown is
        signing. -->
        <role>Chief Executive Officer</role>
      </signatory>
    </signatory>
    
    <signatory>
      <name><ref to="Purchaser" /></name>
      <signatory>
        <name>Marty McFly</name>
        <role>President</role>
      </signatory>
    </signatory>
  </signatories>
</doc>
```

A few notes:

* LAML permits the usage of the following HTML elements to format or add semantic meaning: `<p>`, `<b>`, `<i>`, `<strong>`, `<em>`, `<table>`, `<tr>`, `<th>`, `<td>`, `<img>`.

* The `<doc>` tag may have `namespace` and `id` attributes. A namespace is simply any globally unique identifier. We recommend using a URL to minimize conflict, but that is not strictly required. An ID should be a unique identifier for this document within its namespace.

  Namespaces and IDs are option but make it easier for documents to reference each other within the same namespace.

Modules
-------

A module is designated by the `<module>` tag. Each module should have either a unique `id` attribute or `name` element to identify it. You can define multiple modules in a LAML file, although it may be easier to organize things if you give each module its own file. Below is an example of a module, with a governing law clause.

```xml
<!-- Each module should have either an id attribute or a name element that
is unique from all other modules. -->
<module id="governing-law-module">
	<name>Governing Law</name>
	
	<!-- Expanded description of what this module contains. The description is
	for the benefit of the author only and will not be incorporated into the
	final legal document -->
	<description>Generic Governing Law Clause</description>
	<body>
	
	  <!-- A section is the basic building block of an agreement -->
		<section id="governing-law-clause">
			<name>Governing Law</name>
			<p>This Agreement and all acts and transactions pursuant hereto and
			the rights and obligations of the parties hereto shall be governed,
			construed and interpreted in accordance with the laws of the State of
			<ref to="Governing Law State" />, without giving effect to principles
			of conflicts of law.</p>
		</section>
	</body>
</module>
```
