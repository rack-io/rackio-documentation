## Trend based Logging

Some variables or tags are required to be monitored in time, Rackio can perform automatic data logging for trends and historical display, you can set the tags and their frequency and Rackio will save these in a local database.

---

## Automatic Data Logging

<div class="admonition note">
    <p class="first admonition-title">Note</p>
    <p class="last">
        This feature is under development process
    </p>
</div>

Tag values can be save to a local database for the next restart of the application in this way you can preserve the state of your automation applications.

```python
db_tags = [
   "P1",
   "P2",
   "F1",
   "F2",
]

app.set_db("tags.db")
app.set_dbtags(db_tags, 1)

```

Defining which tags to be saved in a list, and the `set_dbtags` method will take this list and the time interval (in seconds) in which the data will be continuously saved.

---