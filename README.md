<details>
<summary>📌 전체 Use-Case 다이어그램&nbsp;(클릭)</summary>

```mermaid
flowchart TD
    %% Actors
    User(("User"))
    AI["AI Service"]
    Mail["Email Service"]

    %% Auth
    subgraph Auth
        User --> Register((Register))
        User --> Login((Login))
    end

    %% Project
    subgraph Project
        User --> CreateProj((Create Project))
        User --> GetProj((Get Project))
        User --> UpdateProj((Update Project))
        User --> DeleteProj((Delete Project))
        User --> SendInvite((Send Invite))
        SendInvite --|이메일| Mail
    end

    %% Node
    subgraph Node
        User --> ListNodes((List Nodes))
        User --> CreateNodes((Create Nodes))
        User --> UpdateNode((Update Node))
        User --> DeleteNode((Delete Node))
        CreateNodes --|GPT-3.5 Turbo| AI
    end

    %% Tag
    subgraph Tag
        User --> CreateTag((Create Tag))
        User --> AttachTag((Attach Tag))
        User --> DetachTag((Detach Tag))
    end

    %% Vote
    subgraph Vote
        User --> CastVote((Cast Vote))
        User --> ConfirmVotes((Confirm Votes))
    end

    %% History
    subgraph History
        User --> SaveSnap((Save Snapshot))
        User --> ViewHist((View History))
    end
</details> ```
