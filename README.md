# Alaska Benchmark datasets

Datasets listed in this page are used and documented in <a href="https://arxiv.org/abs/2101.11259">Alaska: A Flexible Benchmark for Data Integration</a>. 

The table below summarizes all the available datasets and corresponding ground truths for the supported tasks (Entity Resolution and Schema Matching).



<table>
<thead>
  <tr>
    <th colspan="4">Dataset</th>
    <th colspan="2">Entity Resolution ground truth</th>
    <th colspan="2">Schema Matching ground truth</th>
    <th></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>Vertical</b></td>
    <td><b>Sources</b></td>
    <td><b>Records</b></td>
    <td><b>Attributes</b></td>
    <td><b>Entities</b></td>
    <td><b>Labeled records</b></td>
    <td><b>Target attributes</b></td>
    <td><b>Labeled attributes</b></td>
    <td><b>Download</b></td>
  </tr>
  <tr>
    <td>Camera</td>
    <td>24</td>
    <td>29,787</td>
    <td>4,660</td>
    <td>103</td>
    <td>3,865</td>
    <td>56</td>
    <td>687</td>
    <td><a href="http://bit.ly/camera_data" target="_blank">Download (8.6 MB)</a></td>
  </tr>
  <tr>
    <td>Monitor</td>
    <td>26</td>
    <td>16,662</td>
    <td>1,687</td>
    <td>232</td>
    <td>2,273</td>
    <td>87</td>
    <td>1,026</td>
    <td><a href="http://bit.ly/monitor_data" target="_blank">Download (3.7 MB)</a></td>
  </tr>
  <tr>
    <td>Notebook</td>
    <td>27</td>
    <td>23,167</td>
    <td>3,099</td>
    <td>208</td>
    <td>1,143</td>
    <td>44</td>
    <td>960</td>
    <td><a href="https://bit.ly/notebook_data_" target="_blank">Download (7.5 MB)</a></td>
  </tr>
</tbody>
</table>



## Data Format

### Dataset

Alaska data sets contain a set of products specifications in JSON format. A specification consists of a list of <attribute_name, attribute_value> pairs and is stored in a file; files are organized into directories, each directory corresponds to a web source (e.g., www.ebay.com).

Example of specification:

```json
{
    "<page title>": "ASUS VT229H & Full Specifications at ebay.com",
    "screen size": "21.5''",
    "brand": "Asus",
    "display type": "LED",
    "dimension": "Dimensions: 19.40 x 8.00 x 11.80 inches",
    "refresh rate": "75hz",
    "general features": "Black",
}
```



### Entity Resolution Ground Truth

The Entity Resolution ground truth is stored in a CSV file with two columns:

* the "entity_id" is a global identifier for a real-world object (e.g., an ASUS VT229H monitor)
* the "spec_id" is a global identifier for a specification and consists of a relative path of the specification file. For instance, the spec_id "www.ebay.com//1000" refers to the 1000.json file inside the www.ebay.com directory

Example of Entity Resolution ground truth:

```
entity_id,spec_id
ENTITY#001,www.ebay.com//14633
ENTITY#001,www.ebay.com//14633
ENTITY#001,www.ebay.com//20380
```



### Schema Matching Ground Truth

The Schema Matching ground truth is stored in a CSV file with two columns:

* the "source_attribute_id" is a global identifier for an attribute at source level. For instance, the source_attribute "www.ebay.com//screen size" refers to all the "screen size" attributes from specifications in source www.ebay.com
* the "target_attribute_name" is the name of the target attribute in the mediated schema (e.g., "brand", "screen_size", etc.)

Example of Schema Matching ground truth:

```
source_attribute_id,target_attribute_name
ca.pcpartpicker.com//response time,response_time
ca.pcpartpicker.com//screen size,screen_size_diagonal
catalog.com//aspect ratio,supported_aspect_ratio
```
