# Twasta sample applications

Ready-to-import sample applications for [Twasta](https://platform.twasta.ai).
Every one is public: anyone with a Twasta account can import it, run it and
adapt it.

This repository is the **catalog**. Each application lives in its own
repository; [`catalog.json`](catalog.json) is the index that Twasta's
**Samples Gallery** reads.

## Available applications

| Application | What it is | Repository |
|---|---|---|
| **Document Management System** | Controlled documents with an approval lifecycle, acknowledgement tracking and an AI assistant that answers from document content. | [`DMS_APP`](https://github.com/Proteus-Technologies-Private-Limited/DMS_APP) |

## Importing one

In Twasta, open **Samples Gallery** and choose an application — that is the
whole flow. To import by hand instead, use **Workbench → Import from Git** with
the repository's `owner/repo` or its full URL.

After importing, **deploy** the project to create its tables. Application data
(rows, uploaded files, users) is per-install and is never carried in a sample
repository; where an application ships demo rows, they are in its
`Sample_Data/` folder.

## Adding an application

1. Create a public repository holding the Twasta project — `application.json`
   at the repository root, with `Metadata_Model/`, `src/` and the rest beside
   it. **Name the repository exactly what the imported project should be
   called**: Twasta names the project after the repository.
2. Strip per-install artifacts. A `.gitignore` covering `.twasta/`,
   `.twasta_plans/`, `.autoagent_state.json`, `.twasta_build_state.json`,
   `.claude/` and `Metadata_Model/connections/` is the baseline — the last one
   matters, connection credentials must never be published.
3. Add a `README.md` describing the application, and optionally
   `Sample_Data/seed.json` with demo rows.
4. Add an entry to [`catalog.json`](catalog.json) here, following
   [`catalog.schema.json`](catalog.schema.json).
5. Topic the application repository `twasta-sample-app`.

The gallery reads `catalog.json` from this repository's default branch, so an
application appears as soon as the entry is merged — no Twasta release needed.
