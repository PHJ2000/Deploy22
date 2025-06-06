<details>
<summary>📌 전체 Use-Case 다이어그램&nbsp;(클릭)</summary>

```mermaid
flowchart TD
  %% Actors
  actor_User(("User"))
  actor_AI(["AI Service"])
  actor_Mail(["Email Service"])

  %% Auth
  subgraph Auth
    actor_User --> Register((Register))
    actor_User --> Login((Login))
  end

  %% Project
  subgraph Project
    actor_User --> CreateProj((Create Project))
    actor_User --> GetProj((Get Project))
    actor_User --> UpdateProj((Update Project))
    actor_User --> DeleteProj((Delete Project))
    actor_User --> SendInvite((Send Invite))
    SendInvite --|이메일| actor_Mail        %% ← 레이블 표기 수정
  end

  %% Node
  subgraph Node
    actor_User --> ListNodes((List Nodes))
    actor_User --> CreateNodes((Create Nodes))
    actor_User --> UpdateNode((Update Node))
    actor_User --> DeleteNode((Delete Node))
    CreateNodes --|GPT-3.5 Turbo| actor_AI  %% ← 레이블 표기 수정
  end

  %% Tag
  subgraph Tag
    actor_User --> CreateTag((Create Tag))
    actor_User --> AttachTag((Attach Tag))
    actor_User --> DetachTag((Detach Tag))
  end

  %% Vote
  subgraph Vote
    actor_User --> CastVote((Cast Vote))
    actor_User --> ConfirmVotes((Confirm Votes))
  end

  %% History
  subgraph History
    actor_User --> SaveSnap((Save Snapshot))
    actor_User --> ViewHist((View History))
  end
</details> ```
