> **Authors:** {{authors}}{{directors}}
> {% if publicationTitle %}**Publication:** *"{{publicationTitle}}"*{% endif %}
> {% if date %}**Date:** {{date | format("YYYY-MM-DD")}}{% endif %}

---
### **Bibliography**
~~~~
{{bibliography}}
~~~~

**Link to Zotero:** {{pdfZoteroLink}}
**Tags:** {{hashTags}}

---
> [!abstract]+ **Abstract**
> > *« {{abstractNote}} »*

---
### **Annotations:**
{% for annotation in annotations %}
<div class="annotation-card" style="padding: 20px; border: 1px solid var(--color-border); border-radius: 12px; margin: 15px 0; font-family: 'Segoe UI', Arial, sans-serif; background: rgba(70, 70, 70, 0.2); backdrop-filter: blur(8px); overflow-wrap: break-word; word-wrap: break-word;">
  <div style="display: flex; align-items: center; margin-bottom: 15px; border-bottom: 1px solid var(--color-border); padding-bottom: 10px;">
    <div style="width: 14px; height: 14px; border-radius: 50%; background-color: {{annotation.color}}; margin-right: 10px;"></div>
    <div style="font-size: 16px; color: var(--interactive-accent); font-weight: bold; text-transform: uppercase; letter-spacing: 1px;">{{annotation.type | capitalize}}</div>
  </div>
  <div style="margin-bottom: 15px; font-size: 14px; color: var(--text-normal); font-weight: bold;">
    {{annotation.comment}}
  </div>
  <div style="font-size: 14px; color: var(--text-normal);">
    {% if annotation.annotatedText %}
    <p style="margin-bottom: 10px; font-style: italic;">“{{annotation.annotatedText}}”</p>
    {% endif %}
    {% if annotation.imageRelativePath %}
    <p style="margin-bottom: 10px;">
      <b>Image:</b>
      <img src="{{annotation.imageRelativePath}}" style="max-width: 100%; height: auto; border-radius: 6px; margin-top: 5px;" />
    </p>
    {% endif %}
<p style="display: flex; flex-wrap: wrap; justify-content: space-between; align-items: center; margin-bottom: 10px; font-weight: bold; word-wrap: break-word;">
  <span style="flex: 1;">
    {% if annotation.hashTags %}
    {% for tag in annotation.hashTags.split(',') %}
    <span style="color: var(--interactive-accent); margin-right: 8px;">

{{ tag }}
    </span>
    {% endfor %}
    {% endif %}
  </span>
  {% if annotation.pageLabel and annotation.desktopURI %}
  <a href="{{annotation.desktopURI}}" style="color: var(--interactive-accent); text-decoration: none; font-weight: bold;">
    Page {{annotation.pageLabel}}
  </a>
  {% elif annotation.pageLabel %}
  <span>Page {{annotation.pageLabel}}</span>
  {% endif %}
</p>
  </div>
</div>{% endfor %}