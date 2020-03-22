# Menu node variables
The following variables are available to use on the object returned by the [HubL menu function](/docs/hubl/functions#menu).
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| node.label | String | The menu label of the page. | 
| node.url | String | URL of the page. | 
| node.pageId | Number | ID of the page if within HubSpot. | 
| node.contentGroupId | Number | Blog ID of the page if it is a HubSpot blog post. | 
| node.parentNode | Object | The parent node of the current node. The parent node will have the current node in its children property. | 
| node.children | List | The list of child nodes for the current node. | 
| node.activeBranch | Boolean | True if the node is in the top-level branch that the current page is in. | 
| node.activeNode | Boolean | True if the node is the current page. | 
| node.level | Number | The number of levels deep the current node is from the top-level nodes. | 
| node.pageTitle | String | Name of the content page if within HubSpot. | 
| node.slug | String | Path slug of the page. | 
| node.linkTarget | String | Link target of the page. | 

