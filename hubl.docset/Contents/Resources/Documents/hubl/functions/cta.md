# cta
Because CTA modules have so many parameters that contain variations of their code, you can use the CTA function to easily generate a particular CTA in a template, page, or email. This function is what the rich text editor uses when you add a CTA via the editor.

#### Example
```jinja2
{{ cta('ccd39b7c-ae18-4c4e-98ee-547069bfbc5b')  }} 
{{ cta('ccd39b7c-ae18-4c4e-98ee-547069bfbc5b', 'justifycenter') }}
```

#### Output
```jinja2
<span class="hs-cta-wrapper" id="hs-cta-wrapper-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b"> 
    <span class="hs-cta-node hs-cta-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b" id="hs-cta-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b" style="visibility: visible;">
        <a id="cta_button_158015_19a9097a-8dff-4181-b8f7-955a47f29826" class="cta_button " href="//cta-service-cms2.hubspot.com/ctas/v2/public/cs/c/?cta_guid=19a9097a-8dff-4181-b8f7-955a47f29826&placement_guid=ccd39b7c-ae18-4c4e-98ee-547069bfbc5b&portal_id=158015&redirect_url=APefjpH34lXcq1H4FhyHhE3DNeHPNigbBluiv6t07-N80GLkyj2Dn9PizhW8bo4ecrS47RmyslLg7QQKWLG7n2oNkvrumL9dWUjMMEjVYvStZ-IMyulMBvdU8AddI6nFXL0G_VPP_VXmnFi66RKPPjPvx6kbyPO6k566noP4CTZMyADHkGsGBf4S95YdTNtTTFabShT62cVAiV_oWlXbpfPWQc4G3IvkoDoAhmpQVW-ggUcKa4Ft_5A&hsutk=683eeb5b499fdfdf469646f0014603b4&utm_referrer=http%3A%2F%2Fwww.davidjosephhunt.com%2F%3Fhs_preview%3DNVkCLfFf-2857453560&canon=http%3A%2F%2Fwww.davidjosephhunt.com%2F-temporary-slug-63bb220d-eda6-44d0-9738-af928e787237" style="" cta_dest_link="http://www.hubspot.com/free-trial" title="Start a HubSpot trial"> Start a HubSpot trial </a>
    </span>
    <script charset="utf-8" src="//js.hscta.net/cta/current.js"></script>
    <script type="text/javascript">
        hbspt.cta.load(158015, 'ccd39b7c-ae18-4c4e-98ee-547069bfbc5b');
    </script>
</span>
<span class="hs-cta-wrapper" id="hs-cta-wrapper-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b"> 
    <span class="hs-cta-node hs-cta-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b" id="hs-cta-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b" style="display: block; text-align: center; visibility: visible;">
        <a id="cta_button_158015_19a9097a-8dff-4181-b8f7-955a47f29826" class="cta_button " href="//cta-service-cms2.hubspot.com/ctas/v2/public/cs/c/?cta_guid=19a9097a-8dff-4181-b8f7-955a47f29826&placement_guid=ccd39b7c-ae18-4c4e-98ee-547069bfbc5b&portal_id=158015&redirect_url=APefjpH34lXcq1H4FhyHhE3DNeHPNigbBluiv6t07-N80GLkyj2Dn9PizhW8bo4ecrS47RmyslLg7QQKWLG7n2oNkvrumL9dWUjMMEjVYvStZ-IMyulMBvdU8AddI6nFXL0G_VPP_VXmnFi66RKPPjPvx6kbyPO6k566noP4CTZMyADHkGsGBf4S95YdTNtTTFabShT62cVAiV_oWlXbpfPWQc4G3IvkoDoAhmpQVW-ggUcKa4Ft_5A&hsutk=683eeb5b499fdfdf469646f0014603b4&utm_referrer=http%3A%2F%2Fwww.davidjosephhunt.com%2F%3Fhs_preview%3DNVkCLfFf-2857453560&canon=http%3A%2F%2Fwww.davidjosephhunt.com%2F-temporary-slug-63bb220d-eda6-44d0-9738-af928e787237" style="" cta_dest_link="http://www.hubspot.com/free-trial" title="Start a HubSpot trial"> Start a HubSpot trial </a>
    </span>
    <script charset="utf-8" src="//js.hscta.net/cta/current.js"></script>
    <script type="text/javascript">
        hbspt.cta.load(158015, 'ccd39b7c-ae18-4c4e-98ee-547069bfbc5b');
    </script>
</span>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| guid | String | The ID of the CTA to render. Can be found in the URL of the details screen of the CTA. | 
| align_opt | Enumeration | Adjusts alignment of CTA. Values include justifyleft, justifycenter, justifyright, justifyfull. | 

