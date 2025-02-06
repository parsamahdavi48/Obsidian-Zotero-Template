> **Authors:** {{authors}}{{directors}}
> {% if publicationTitle %}**Publication:** *"{{publicationTitle}}"*{% endif %}
> {% if date %}**Date:** {{date | format("YYYY-MM-DD")}}{% endif %}

---
### **Bibliography**
~~~~
{{bibliography}}
~~~~

**Link to Zotero:** {{pdfZoteroLink}}   
**Tags:** {{hashTags}}, {% for annotation in annotations %}{% if annotation.hashTags %}{{annotation.hashTags}}, {% endif %}{% endfor %}

---

> [!abstract]+ **Abstract**
> > *{{abstractNote}}*

---
### **Annotations:**
{% for annotation in annotations %}

##### **{{annotation.type | capitalize}}**  

**Comment:** {{annotation.comment}}

{% if annotation.annotatedText %}
**Annotated:** *“{{annotation.annotatedText}}”*
{% endif %}

{% if annotation.imageRelativePath %}
![[{{annotation.imageRelativePath}}]]
{% endif %}

**Tags:** {% if annotation.hashTags %}{{annotation.hashTags}}{% endif %}  
{% if annotation.pageLabel %} **Page:**  {% if annotation.desktopURI %} [{{annotation.pageLabel}}]({{annotation.desktopURI}})  
{% else %} {{annotation.pageLabel}}  
{% endif %}{% endif %}

---
{% endfor %}
