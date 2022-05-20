# Group chat
Group chats are meant to be private ad-hoc groups.

# Rules

### Glossary
Group creator - one who creates new group  
Member - anyone in the group  
Admin - group administrator  
User - Member who is not an Admin  

## Group creation
Group creator is only allowed to add mutual contacts. This is important, both for privacy and as a spam prevention measure.
- Group chat MUST contain at least one Member
- Group chat MUST be composed only of Group creator's mutual contacts
- Group creator MUST become an Admin of the group

## Group roles
- Group chat CAN have more than one Admin
- Only Admin CAN promote User to the Admin role

## Members addition
- New group member CAN only be added by Admin
- New group member MUST be Admin's mutual contact

## Members removal
- Only Admin CAN remove User
- Member CAN leave the group
- When last Admin leaves the group, User who was added first MUST become an Admin

## Messages visibility
- Member added to the group MUST NOT see messages prior that event and MUST see all messages post that event

## Group appearance
- Only Admin CAN change the name of the group
- Only Admin CAN change the image of the group
- Only Admin CAN change the color of the group
- Unless explicitly changed, group name MUST follow given pattern:
  - 1 Member: "{$Member1Name}"
  - 2 Members: "{$Member1Name}&{$Member2Name}"
  - \>2 Members: "{$Member1Name}, ..., {$MemberNName}"

## Link invitations (deprecated Mobile feature)
This feature is going to be removed after breaking change adaptation period (3-6 months from now).
- Admin CAN share group chat invitation link
- Any Status User CAN request access to the group through the invitation link
- Only Admin CAN approve or reject User's invitation request

# Behavior
Group chat behavior should follow Figma designs: https://www.figma.com/file/17fc13UBFvInrLgNUKJJg5/Kuba%E2%8E%9CDesktop?node-id=112%3A26519
