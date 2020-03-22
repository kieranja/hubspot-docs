# CTA
A Call to Action or CTA module allows users to add a HubSpot Call to Action button to a predefined area of a page.

#### Example
```jinja2
{% cta "cta" %}
{% cta "my_cta" label='Select a CTA', guid='ccd39b7c-ae18-4c4e-98ee-547069bfbc5b', image_src='https://no-cache.hubspot.com/cta/default/53/c7335b66-a0d4-4d19-82eb-75e1626d02d0.png' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_cta" style="" data-hs-cos-general-type="widget" data-hs-cos-type="cta">
	<!--HubSpot Call-to-Action Code --> 
	<span class="hs-cta-wrapper" id="hs-cta-wrapper-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b">
		<span class="hs-cta-node hs-cta-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b" id="hs-cta-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b" style="visibility: visible;">
			<a id="cta_button_158015_19a9097a-8dff-4181-b8f7-955a47f29826" class="cta_button " href="//cta-service-cms2.hubspot.com/ctas/v2/public/cs/c/?cta_guid=19a9097a-8dff-4181-b8f7-955a47f29826&placement_guid=ccd39b7c-ae18-4c4e-98ee-547069bfbc5b&portal_id=158015&redirect_url=APefjpFSOqhysLBE-Yye5WFoP82Swxb2PVWpfI3VxlUjuOCHfiVMcxKic3yM28vuwu9UB8_Jyhk6DGRCEN63hKqQOMtMTGmQZ1UNMK3LtNx0sRrAfQQYna2BfZ9RmgQOs8sKO_PcKOP6G26L5wQ5vdcXXOiMCxFPJxzPzUCcl474iiHKbEo5H8LVtZf6e140VOSGJ37NTpxCcPHLDvH9iFaT6mR0BnKzFReaX0FXBj7Lx2rFLVCZcIC0bdaFEGI1uKOJBMNT9RDtEzeJzUHzFYN0b34uv-ZR4w&hsutk=683eeb5b499fdfdf469646f0014603b4&utm_referrer=http%3A%2F%2Fwww.davidjosephhunt.com%2Fvariables%3Fhs_preview%3D159bC1Cj-2863569740&canon=http%3A%2F%2Fwww.davidjosephhunt.com%2Fvariables" style="" cta_dest_link="http://www.hubspot.com/free-trial" title="Start a HubSpot trial"> Start a HubSpot trial </a>
		</span>
		<script charset="utf-8" src="//js.hscta.net/cta/current.js"></script>
		<script type="text/javascript">
			hbspt.cta.load(158015, 'ccd39b7c-ae18-4c4e-98ee-547069bfbc5b');    
		</script>
	</span>  
	<!-- end HubSpot Call-to-Action Code -->
</span>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| embed_code | String | The embed code for the CTA. \n differentiates line breaks. | 
| full_html | String | The embed code for the CTA (Same as embed_code). \n differentiates line breaks. | 
| image_src | String | Image src url that defines the preview image in the content editor. | 
| image_editor | String | Markup for the image editor preview | 
| guid | String | The unique ID number of the CTA. This ID number is available in the URL of the Details screen of a particular CTA. This parameter is used to choose which CTA to display by default. | 
| image_html | String | CTA image HTML without the CTA script.* | 
| image_email | String | Email-friendly version of the CTA code.* | 

