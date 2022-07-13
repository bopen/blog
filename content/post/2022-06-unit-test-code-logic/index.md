---
title: "Unit Test Code Logic"
subtitle: ""
summary: ""
authors:
- alexamici
tags:
- testing
- best-practices
categories: []
date: 2022-06-26T18:39:05+02:00
lastmod: 2022-06-26T18:39:05+02:00
featured: false
draft: true

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---

A lot of rules and best practices in testing are based on a single idea,
something along the line: "keep the interesting code close and away from
other code".

Let's try to use and example to define the "interesting code" bit.

The following code is run within an API request and fetches the data for
the response from a database. This is similar to functions I have seen
in several projects and looks relatively harmless.

```python
from . import model

pretty_print_data_type = { ... }


def fetch_from_store(request: fastapi.Request) -> dict[str, Any]:
    data = model.Data.query(data_type=request.data_type)

    hemisphere_code = "6" if data.hemisphere == "N" else "7"
    data_epsg = f"EPSG36{hemisphere_code}{data.zone}"

    data_uuid = f"{pretty_print_data_type[data_type]}-{data.uid}"

    data = {
        "data_uuid": data_uuid,
        "data_epsg": data_epsg,
        ...
    }

    return data
```

The queries the database applying the filter in the HTTP request and
lightly reformats the data in the database to the expected output in
response.

As it is it the code is a small nightmere to test, because you need to make stubs
for both the fastapi Request and for the SQLAlchemy query, and the "interesting code"
that needs tesing has nothing to do with either of the two!

The interesting logic bits that needs careful testing are:
1. the computation of `data_epsg`
1. the computation of `data_uuid`

These are string manipulations with a few conditional and several corner cases,
and have nothing to do with FastAPI or SQLAlchemy. The logic can (and should)
be tested with just strings and without any mock.

The rest of the function only need testing that it uses current interfaces,
as there is no moving part (conditionals, loops, handled exceptions, etc).
