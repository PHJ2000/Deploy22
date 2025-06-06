<details>
<summary>📌 전체 Use-Case 다이어그램 (클릭해서 펼치기)</summary>
%% BRAINNET - Use-Case Diagram
%% --------------------------------------------------
%%  Actors
actor Guest
actor User
actor "AI Service" as AI
actor "Email Service" as Mail

%%  1. Auth
rectangle "Auth" {
  Guest -- (Register)
  Guest -- (Login)
  User  -- (Logout)
}

%%  2. 계정 정보
rectangle "Account" {
  User -- (View Profile)          : GET /users/me
  User -- (View Tag Summaries)    : GET /users/me/tag-summaries
}

%%  3. Project 흐름
rectangle "Project" {
  User -- (List Projects)         : GET /projects
  User -- (Create Project)        : POST /projects
  User -- (Get Project)           : GET /projects/{id}
  User -- (Update Project)        : PUT·PATCH /projects/{id}
  User -- (Delete Project)        : DELETE /projects/{id}
  User -- (Invite User to Project): POST /projects/{id}/invite
  User -- (Join Project)          : POST /projects/join
  User -- (View Project Summary)  : GET /projects/{id}/summary
}

%%  4. Node 관리
rectangle "Node" {
  User -- (List Nodes)            : GET /projects/{id}/nodes
  User -- (Create Nodes)          : POST /projects/{id}/nodes
  User -- (Update Node)           : PATCH /projects/{id}/nodes/{nid}
  User -- (Delete Node)           : DELETE /projects/{id}/nodes/{nid}
  User -- (Activate Node)         : POST /projects/{id}/nodes/{nid}/activate
  User -- (Deactivate Node)       : POST /projects/{id}/nodes/{nid}/deactivate
  (Create Nodes) ..> AI : "GPT-3.5 Turbo\n연관 아이디어"
}

%%  5. Tag 관리
rectangle "Tag" {
  User -- (List Tags)             : GET /projects/{id}/tags
  User -- (Create Tag)            : POST /projects/{id}/tags
  User -- (Get Tag)               : GET /projects/{id}/tags/{tid}
  User -- (Update Tag)            : PATCH /projects/{id}/tags/{tid}
  User -- (Delete Tag)            : DELETE /projects/{id}/tags/{tid}
  User -- (Attach Tag to Node)    : POST /projects/{id}/tags/{tid}/nodes/{nid}
  User -- (Detach Tag from Node)  : DELETE /projects/{id}/tags/{tid}/nodes/{nid}
}

%%  6. 투표
rectangle "Vote" {
  User -- (Cast Vote)             : POST /projects/{id}/tags/{tid}/vote
  User -- (Confirm Votes)         : POST /projects/{id}/votes/confirm
}

%%  7. 히스토리
rectangle "History" {
  User -- (List History)          : GET /projects/{id}/history
  User -- (Get History Entry)     : GET /projects/{id}/history/{eid}
}

%%  외부 서비스 연결
(Invite User to Project) ..> Mail : "초대 이메일 발송"
</details>
