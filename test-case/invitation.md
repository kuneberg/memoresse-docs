## 1. Generate Invitation (Owner Side)

### Behavior - Web
- Owner creates a Person in their account
- Owner clicks **"Invite"** button for the Person
- Invitation link is generated
- Link is displayed as selectable text
- **"Copy"** button copies link to clipboard
- **"Delete"** button revokes the invitation

### Behavior - iOS App
- Owner creates a Person in their account
- Owner clicks **"Invite"** button for the Person
- Invitation link is generated
- Link doesn't display as selectable text
- **"Share invitation link"** button opens native iOS share sheet
- **"Delete"** button revokes the invitation

### What to Verify
- Only one active invitation per Person at a time
- Existing active invitation is reused (no duplicate invitations)
- Invitation URL format: `{appUrl}/invitation?key={uuid}`
- Copy/Share functionality works correctly per platform
- Loading indicator appears while generating
- Delete button removes/revokes invitation
- Invitation appears only for Persons without attached account

---

## 2. Accept Invitation (Recipient Side)

### Behavior - All Platforms
- Recipient opens invitation link
- Recipient must be logged in to respond
- Recipient doesn't sees invitation details
- Recipient clicks **"Accept"** button
- Person is attached to Recipient's account
- New Person created in Recipient's account pointing to Sender's account

### What to Verify
- Recipient cannot accept their own invitation
- New Person created in Recipient's account with:
  - Name = Owner's name
  - attachedAccountId = Owner's account ID
- Owner sees "connected to a real user account" status

---

## 3. Reject Invitation (Recipient Side)

### Behavior - All Platforms
- Recipient opens invitation link
- Recipient sees invitation details
- Recipient clicks **"Reject"** button
- Person remains unattached
- No Person created in Recipient's account

### What to Verify
- No Person created in Recipient's account

---

## 4. Revoke Invitation (Owner Side)

### Behavior - All Platforms
- Owner clicks **"Delete"** button on active invitation
- Invitation status changes to **REVOKED**
- Invitation link becomes invalid
- Recipient cannot respond to revoked invitation

### What to Verify
- Revoked invitation cannot be accepted/rejected
- Owner can generate new invitation after revoking

---

## 5. Detach Account (Owner Side)

### Behavior - All Platforms
- Owner sees "connected to a real user account" when Person has attached Account
- Owner clicks **"Detach"** button
- Confirmation dialog appears
- Person becomes unattached
- Owner can send new invitation

### What to Verify
- Detach button appears only when Person has attached account
- Confirmation dialog prevents accidental detach
- Person.attachedAccountId is cleared after detach
- Invite button reappears after detach
- Detach does not delete the Person

---

## 6. Invitation Link Behavior

### What to Verify
- Invitation link format: `{appUrl}/invitation?key={uuid}`
- Key is unique UUID for each invitation
- Opening invalid link shows appropriate error
- Opening old revoked link falls back to newer active invitation (if exists)

---

## 7. Edge Cases

### Platform-Specific
- iOS: Share button uses native share sheet with position origin
- Web: Copy button with clipboard API
- Both platforms show delete button
- Both platforms show same invitation status
