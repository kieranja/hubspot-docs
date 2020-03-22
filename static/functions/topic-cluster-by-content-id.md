# topic_cluster_by_content_id
Returns a HubL dict representing the topic cluster associated with a piece of content (determined by the passed content id), including metadata about the associated pillar page, core topic, and subtopics. Can be used to "auto-link" a piece of content with its associated pillar page \[if it exists\].

Available metadata can be found in: attachableContent (the current content's metadata), topic (the current content's associated topic metadata), coreTopic (the associated cluster's core topic metadata), and pillarPage (the associated pillar page's metadata).

Use `{{ topicCluster|pprint }}` to see a full a display of available properties/attributes.

#### Example
```jinja2
{{ topic_cluster_by_content_id(content.id) }}
{%- if content.id -%}
  {%- set topicCluster = topic_cluster_by_content_id(content.id) -%}
  {%- if topicCluster.pillarPage.url.value and topicCluster.pillarPage.publishState == 'PUBLISHED' -%}
    <div>Topic: <a href="{{ topicCluster.pillarPage.url.value }}">{{ topicCluster.coreTopic.phrase }}</a></div> 
  {%- endif -%}
{%- endif -%}
```

#### Output
```jinja2
{ attachedContent, topic, coreTopic, pillarPage }
(AttachedContentWithContext:  {attachedContent=AttachedContent{id=1234,    topicId=1234,    clusterId=1234,    portalId=0,    attachable=Attachable{contentId=124,    url=ValidatedUri{https://www.hubspot.com/},  attachableType=LANDING_PAGE,  title=title,  publishState=PUBLISHED,  deletedAt=null},  isLinkedToPillarPage=null,  isPillarPage=null,  createdAt=1547238986475,  updatedAt=1547238986475,  deletedAt=null},  coreTopic=Optional[Topic{id=1234,    portalId=0,    clusterId=1234,    phrase=TOPIC PHRASE,    attachedContent=null,    isCoreTopic=false,    createdAt=1547157062081,    updatedAt=1547232313421,    deletedAt=null}],  pillarPage=Optional[AttachedContent{id=1234,    topicId=1234,    clusterId=1234,    portalId=0,    attachable=Attachable{contentId=null,    url=ValidatedUri{https://www.hubspot.com.com/},  attachableType=EXTERNAL_URL,  title=null,  publishState=PUBLISHED,  deletedAt=null},  isLinkedToPillarPage=null,  isPillarPage=null,  createdAt=1547157062086,  updatedAt=1547157062086,  deletedAt=null}],  topic=Optional[Topic{id=1234,    portalId=0,    clusterId=8345,    phrase=topic phrase,    attachedContent=null,    isCoreTopic=false,    createdAt=1547238962703,    updatedAt=1547238962703,    deletedAt=null}]})



<div>
  Topic: <a href="#-link-to-pillar-page-url">
    core topic phrase
  </a>
</div>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| content_id | Id | The id of the page to look up. | 

