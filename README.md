# SignalMesh
A springboot-based observability and log analysis platform that collects, searches, filters and analyse application logs using elastic search

**Phase 1 — Infra**
- Install Docker Desktop (if not already installed)
- Create `docker-compose.yml` with the OpenSearch config
- Run `docker-compose up -d`
- Check `localhost:9200` in browser — should show JSON

**Phase 2 — Data layer**
- Create index `logs-v1` with a mapping (timestamp=date, level/service=keyword, message=text)
- Add 3-4 fake log docs manually via curl/Postman
- Confirm the docs show up when you query OpenSearch directly

**Phase 3 — Backend service**
- New Spring Boot project, add `opensearch-java` dependency
- Config class → OpenSearch client bean (`localhost:9200`)
- Build `POST /logs` (bulk-index incoming logs)
- Build `GET /search` (query by text + time range)
- Build `GET /aggregate` (count/avg/group by field)
