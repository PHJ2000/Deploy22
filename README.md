<details>
<summary>📌 전체 Use-Case 다이어그램&nbsp;(클릭해서 펼치기)</summary>

```mermaid
%% BRAINNET – Use-Case Diagram
actor User
actor "AI Service" as AI
actor "Email Service" as Mail

rectangle Auth {
  User -- (Register)
  User -- (Login)
}

rectangle Project {
  User -- (Create Project)
  User -- (Get Project)
  User -- (Update Project)
  User -- (Delete Project)
  User -- (Send Invite)
  (Send Invite) ..> Mail : 이메일
}

rectangle Node {
  User -- (List Nodes)
  User -- (Create Nodes)
  User -- (Update Node)
  User -- (Delete Node)
  (Create Nodes) ..> AI : GPT-3.5 Turbo
}

rectangle Tag {
  User -- (Create Tag)
  User -- (Attach Tag)
  User -- (Detach Tag)
}

rectangle Vote {
  User -- (Cast Vote)
  User -- (Confirm Votes)
}

rectangle History {
  User -- (Save Snapshot)
  User -- (View History)
}

</details>
