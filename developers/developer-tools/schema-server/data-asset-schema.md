---
description: The standard for describing a Data Asset
---

# Data Asset Schema

Document Templates for Data Assets use a structured data format, based on open schemas \(mainly [schema.org](https://schema.org)\), to describe any type of data asset that exists within the Internet of Impact.

### Types of data assets

* A structured object, such as verifiable claim, with a data model that can be processed using a specific tool or algorithm
* An algorithm for processing or transforming data
* A table or a CSV file with some data
* An organised collection of tables
* A search query
* A collection of files which are related in a way that provides a meaningful dataset
* Images capturing data
* Files relating to machine learning, such as trained parameters or neural network structure definitions
* Anything else that looks like a data asset!

### The standard data model \(schema\) for data assets

The ixo standard for data assets is compatible with mainstream Web 2.0 [guidelines for dataset providers](https://developers.google.com/search/docs/data-types/dataset) to describe their data in a way that search engines, such as Google, can better understand the content of their pages. It is based on the principle that data assets are easier to find and use when they are described with metadata such as their name, description, creator and distribution formats.

The Page Schema for describing a data asst in its ixo Document uses the  [schema.org Dataset markup](https://schema.org/Dataset). 

#### Dataset example

If the Data Asset is a Dataset, we would use the [schema.org/Dataset](https://schema.org/Dataset) definition of  `Dataset`. This includes information about the publication of the dataset, such as the license, when it was published, its [DOI](https://en.wikipedia.org/wiki/Digital_object_identifier), or a `sameAs` pointing to a canonical version of the dataset in a different repository. Add `identifier`, `license`, and `sameAs` for datasets that provide provenance and license information.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Required properties</th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>description</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/Text"><code>Text</code></a>
        </p>
        <p>A short summary describing a dataset.</p>
        <p><b>Guidelines</b>
        </p>
        <ul>
          <li>The summary must be between 50 and 5000 characters long.</li>
          <li>The summary may include Markdown syntax. Embedded images need to use absolute
            path URLs (instead of relative paths).</li>
          <li>When using the JSON-LD format, denote new lines with <code>\n</code> (two
            characters: backslash and lower case letter &quot;n&quot;).</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>name</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/Text"><code>Text</code></a>
        </p>
        <p>A descriptive name of a dataset. For example, &quot;Snow depth in Northern
          Hemisphere&quot;.</p>
      </td>
    </tr>
  </tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">Recommended properties</th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>alternateName</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/Text"><code>Text</code></a>
        </p>
        <p>Alternative names that have been used to refer to this dataset, such as
          aliases or abbreviations. Example (in JSON-LD format):</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>creator</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/Person"><code>Person</code></a> or <a href="https://schema.org/Organization"><code>Organization</code></a>
        </p>
        <p>The creator or author of this dataset. To uniquely identify individuals,
          use <a href="https://orcid.org/">ORCID ID</a> as the value of the <code>sameAs</code> property
          of the <code>Person</code> type. To uniquely identify institutions and organizations,
          use <a href="https://ror.org/">ROR ID</a>. Example (in JSON-LD format):</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>citation</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/Text"><code>Text</code></a> or <a href="https://schema.org/CreativeWork"><code>CreativeWork</code></a>
        </p>
        <p>Identifies academic articles that are recommended by the data provider
          be cited in addition to the dataset itself. Provide the citation for the
          dataset itself with other properties, such as <code>name</code>, <code>identifier</code>,<code>creator</code>,
          and <code>publisher</code> properties. For example, this property can uniquely
          identify a related academic publication such as a data descriptor, data
          paper, or an article for which this dataset is supplementary material for.
          Examples (in JSON-LD format):</p>
        <p><b>Additional guidelines</b>
        </p>
        <ul>
          <li>Don&#x2019;t use this property to provide citation information for the
            dataset itself. It is intended to identify related academic articles, not
            the dataset itself. To provide information necessary to cite the dataset
            itself use <code>name</code>, <code>identifier</code>, <code>creator</code>,
            and <code>publisher</code> properties instead.</li>
          <li>
            <p>When populating the citation property with a citation snippet, provide
              the article identifier (such as a DOI) whenever possible.</p>
            <p>Recommended: <code>&quot;Doe J (2014) Influence of X. Biomics 1(1). https://doi.org/10.1111/111&quot;</code>
            </p>
            <p>Not recommended: <code>&quot;Doe J (2014) Influence of X. Biomics 1(1).&quot;</code>
            </p>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>hasPart</code> or <code>isPartOf</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/URL"><code>URL</code></a> or <a href="https://schema.org/Dataset"><code>Dataset</code></a>
        </p>
        <p>If the dataset is a collection of smaller datasets, use the <code>hasPart</code> property
          to denote such relationship. Conversly, if the dataset is part of a larger
          dataset, use <code>isPartOf</code>. Both properties can take the form of
          a URL or a <code>Dataset</code> instance. In case <code>Dataset</code> is used
          as a value it has to include all of the properties required for a standalone <code>Dataset</code>.
          Examples:</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>identifier</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/URL"><code>URL</code></a>, <a href="https://schema.org/Text"><code>Text</code></a>,
          or <a href="https://schema.org/PropertyValue">PropertyValue</a>
        </p>
        <p>An identifier, such as a DOI or a Compact Identifier. If the dataset has
          more than one identifier, repeat the <code>identifier</code> property. If
          using JSON-LD, this is represented using JSON list syntax.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>keywords</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/Text"><code>Text</code></a>
        </p>
        <p>Keywords summarizing the dataset.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>license</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/URL"><code>URL</code></a>, <a href="https://schema.org/CreativeWork"><code>CreativeWork</code></a>
        </p>
        <p>A license under which the dataset is distributed. For example:</p>
        <p><b>Additional guidelines</b>
        </p>
        <ul>
          <li>
            <p>Provide a URL that unambiguously identifies a specific version of the
              license used.</p>
            <p>Recommended</p><pre><code class="lang-text">&quot;license&quot; : &quot;https://creativecommons.org/licenses/by/4.0&quot;</code></pre>

            <p>Not recommended</p><pre><code class="lang-text">&quot;license&quot; : &quot;https://creativecommons.org/licenses/by&quot;</code></pre>

          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>sameAs</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/URL"><code>URL</code></a>
        </p>
        <p>URL of a reference Web page that unambiguously indicates the dataset&apos;s
          identity, usually in a different repository.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>spatialCoverage</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/Text"><code>Text</code></a>, <a href="https://schema.org/Place">Place</a>
        </p>
        <p>You can provide a single point that describes the spatial aspect of the
          dataset. Only include this property if the dataset has a spatial dimension.
          For example, a single point where all the measurements were collected,
          or the coordinates of a bounding box for an area.</p>
        <p><b>Points</b>
        </p>
        <p><b>Shapes</b>
        </p>
        <p>Use <a href="https://schema.org/GeoShape">GeoShape</a> to describe areas
          of different shapes. For example, to specify a bounding box.</p>
        <p><b>Points inside <code>box</code>, <code>circle</code>, <code>line</code>, or <code>polygon</code> properties must be expressed as a space separated pair of two values corresponding to latitude and longitude (in that order).</b>
        </p>
        <p><b>Named locations</b>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>temporalCoverage</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/Text"><code>Text</code></a>
        </p>
        <p>The data in the dataset covers a specific time interval. Only include
          this property if the dataset has a temporal dimension. Schema.org uses
          the ISO 8601 standard to describe time intervals and time points. You can
          describe dates differently depending upon the dataset interval. Indicate
          open-ended intervals with two decimal points (<code>..</code>).</p>
        <p><b>Single date</b>
        </p>
        <p><b>Time period</b>
        </p>
        <p><b>Open-ended time period</b>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>variableMeasured</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/Text"><code>Text</code></a>, <a href="https://schema.org/PropertyValue"><code>PropertyValue</code></a>
        </p>
        <p>The variable that this dataset measures. For example, temperature or pressure.The
          <a
          href="https://pending.webschemas.org/variableMeasured"><code>variableMeasured</code>
            </a>property is proposed and pending standardization at schema.org. We encourage
            publishers to share any feedback on this property with the schema.org community.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>version</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/Text"><code>Text</code></a>, <a href="https://schema.org/Number"><code>Number</code></a>
        </p>
        <p>The version number for the dataset.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>url</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/URL"><code>URL</code></a>
        </p>
        <p>Location of a page describing the dataset.</p>
      </td>
    </tr>
  </tbody>
</table>#### `DataCatalog` <a id="publication"></a>

The full definition of `DataCatalog` is available at [schema.org/DataCatalog](https://schema.org/DataCatalog).

Datasets are often published in repositories that contain many other datasets. The same dataset can be included in more than one such repository. You can refer to a data catalog that this dataset belongs to by referencing it directly.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Recommended properties</th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>includedInDataCatalog</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/DataCatalog"><code>DataCatalog</code></a>
        </p>
        <p>The catalog to which the dataset belongs.</p>
      </td>
    </tr>
  </tbody>
</table>#### `DataDownload` <a id="download"></a>

The full definition of `DataDownload` is available at [schema.org/DataDownload](https://schema.org/DataDownload). In addition to Dataset properties, add the following properties for datasets that provide download options.

The `distribution` property describes how to get the dataset itself because the URL often points to the landing page describing the dataset. The `distribution` property describes where to get the data and in what format. This property can have several values: for instance, a CSV version has one URL and an Excel version is available at another.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Required properties</th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>distribution.contentUrl</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/URL"><code>URL</code></a>
        </p>
        <p>The link for the download.</p>
      </td>
    </tr>
  </tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">Recommended properties</th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>distribution</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/DataDownload"><code>DataDownload</code></a>
        </p>
        <p>The description of the location for download of the dataset and the file
          format for download.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>distribution.encodingFormat</code>
      </td>
      <td style="text-align:left">
        <p><a href="https://schema.org/Text"><code>Text</code></a>, <a href="https://schema.org/URL"><code>URL</code></a>
        </p>
        <p>The file format of the distribution.</p>
      </td>
    </tr>
  </tbody>
</table>#### Tabular datasets

A [tabular dataset](https://www.w3.org/TR/tabular-data-model/#intro) is one organised primarily in terms of a grid of rows and columns. For pages that embed tabular datasets, you can also create more explicit markup, building on the basic approach described above. 

### Attribution and further resources

The structured data model for ixo data assets builds on schema.org and [Google Developer](https://developers.google.com/search/docs/data-types/dataset) guidelines. To build and test Data Asset templates, a great resource is Google's [Structured Data Markup Helper](https://www.google.com/webmasters/markup-helper/).



