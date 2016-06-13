---
layout: post
title:  Model change
tags:
- Blog
- Post
---

While talking with the people in the lab I found out out that each Cell is unique to the CellPanel (ie. one Cell can only belong to one CellPanel). I had to change the model for Cell and CellPanel to reflect this in models.py.

<pre>
<code>
# Createed model for Cell-Panel.
class CellPanel(models.Model):
    type = models.CharField(max_length=100, blank=False)
    manufacturer = models.CharField(max_length=100, blank=False)
    lot = models.CharField(max_length=100, blank=False)
    expiry = models.DateTimeField(null=True)
    sheet = models.BinaryField()
    created_at = models.DateTimeField(auto_now_add=True, null=True)

    class Meta:
        unique_together = ('type', 'manufacturer', 'lot')

    def __str__(self):
        return "My CellPanel type %s" % (self.type)


# Createed model for Cell. One Cell always belongs to only one CellPanel.
class Cell(models.Model):
    number = models.IntegerField()
    type = models.CharField(max_length=100, blank=False)
    lot = models.CharField(max_length=100, blank=False)
    expiry = models.DateTimeField(null=True)
    created_at = models.DateTimeField(auto_now_add=True, null=True)
    cell_panel = models.ForeignKey(CellPanel)

    class Meta:
        unique_together = ('number', 'cell_panel')

    def __str__(self):
return "My cell number %s in %s" % (self.number, self.type)
</code>
</pre>
