---
layout: post
title: git tracking and deleting remote branches
date: 2009-07-20 09:11
comments: true
categories:
- git
- source control
- version control
---
<strong>List the remote branches that exist for a repository you have cloned:</strong>

	git remote show origin

<strong>Create a local branch that tracks one of the remote branches and then use that local branch:</strong>

	git checkout --track -b name_of_local_branch origin/name_of_remote_branch

If you have not done a pull since someone else created the remote branch, you may first need to do:

	git fetch

<strong>Remove <em>branch</em> from <em>repo</em>.</strong>

<code>git push {repo} :heads/{branch}</code>

Ex: <code>git push origin :somebranch</code>
removes somebranch
