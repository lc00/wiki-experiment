## Overview

* Data is stored in bson, which binary JSON.
* Mongo creates databases and connections on save. No need to explicitly create anything.
* Documents with arrays have a `__v` property that indicates whether some of the indexes might have shifted.

## RDBMS Equivalents

* Collections = Tables
* Documents = Records
* Keys = Columns
