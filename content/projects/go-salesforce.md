+++
title = "Go-Salesforce"
date = 2024-06-03T10:51:02-04:00
weight = 10
description = "Open source REST API wrapper written in Go"
tags = ['salesforce', 'golang']
draft = false
+++

Open source REST API wrapper written in Go.

<div style="display: flex; width: 35%;">
    <a style="margin: auto; margin-left: 0px; padding: 0px 2px 0px 2px;" href="https://github.com/k-capehart/go-salesforce"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=whitef" alt="Link to Github repo"></a>
    <a style="margin: auto; margin-left: 0px; padding: 0px 2px 0px 2px;" href="https://godoc.org/github.com/k-capehart/go-salesforce"><img src="https://godoc.org/github.com/k-capehart/go-salesforce?status.png" alt="Link to go doc"></a>
</div>

- Language: Go
- Allow Golang developers to easily call Salesforce REST API endpoints to authenticate to an org and manipulate data
- Utilizes [go-soql](https://github.com/forcedotcom/go-soql), a package created by Salesforce for marshalling SOQL queries
- Batch requests together to insert, update, upsert, or delete large amounts of records with or without the Bulk API
- Composite Requests group multiple sub-requests into a single request