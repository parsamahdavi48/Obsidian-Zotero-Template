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
> > *« {{abstractNote}} »*

---
### **Annotations:**
{% for annotation in annotations %}
<div class="annotation-card">
  <div class="annotation-header">
    <div class="annotation-color" style="background-color: {{annotation.color}};"></div>
    <div class="annotation-type">{{annotation.type | capitalize}}</div>
  </div>
  <div class="annotation-comment">
    {{annotation.comment}}
  </div>
  <div class="annotation-body">
    {% if annotation.annotatedText %}
    <p class="annotated-text">“{{annotation.annotatedText}}”</p>
    {% endif %}
    {% if annotation.imageRelativePath %}
    <p class="annotation-image">
      <b>Image:</b>
      <img src="{{annotation.imageRelativePath}}" alt="Annotation image" />
    </p>
    {% endif %}
    <p class="annotation-footer">
      <span class="annotation-tags">
        {% if annotation.hashTags %}
        {% for tag in annotation.hashTags.split(',') %}
        <span class="tag">{{ tag }}</span>
        {% endfor %}
        {% endif %}
      </span>
      {% if annotation.pageLabel and annotation.desktopURI %}
      <a href="{{annotation.desktopURI}}" class="annotation-page">
        Page {{annotation.pageLabel}}
      </a>
      {% elif annotation.pageLabel %}
      <span class="annotation-page">Page {{annotation.pageLabel}}</span>
      {% endif %}
    </p>
  </div>
</div>
{% endfor %}
