+++
title = 'Go-Salesforce'
date = 2024-06-03T10:51:02-04:00
weight = 10
description = 'Open source REST API wrapper written in Go'
tags = ['salesforce', 'golang']
pageName = "go-salesforce"
icon = 'data'
draft = false
+++

<div style="display: flex; flex-direction: row;">
    <div style="margin-right: 10px;"><a href="https://github.com/k-capehart/go-salesforce"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=whitef" alt="Link to Github repo"></a></div>
    <div style="margin: auto 0px auto 0px"><a href="https://godoc.org/github.com/k-capehart/go-salesforce"><img src="https://godoc.org/github.com/k-capehart/go-salesforce?status.png" alt="Link to go doc"></a></div>
</div>

Open source REST API wrapper written in Go.

- Language: Golang
- Allow Golang developers to easily call Salesforce REST API endpoints to authenticate to an org and manipulate data
- Utilizes [go-soql](https://github.com/forcedotcom/go-soql), a package created by Salesforce for marshalling SOQL queries
- Batch requests together to insert, update, upsert, or delete large amounts of records with or without the Bulk API
- Composite Requests group multiple sub-requests into a single request