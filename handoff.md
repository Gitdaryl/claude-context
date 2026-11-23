## Session: 2026-11-23 ET
**Environment:** Antigravity IDE
**What was done:**
- Holly Griewahn: Yeti supplied the Michigan LARA record for Holly Griewahn Realty, LLC (state ID 802532824, Active, good standing, filed 10/07/2020; registered office 2162 Christopher St, Adrian MI 49221; mailing PO Box 295, Manitou Beach MI 49253). Screenshot filed at ~/Archive/Clients/Holly-Foundation-Realty/business-records/.
- The record confirms the address already in /root/holly-a2p/register.py on the VPS. Script patched: address note updated, and it now refuses 802532824 at the EIN prompt (the state ID is 9 digits and looks like an EIN but is not one). Backup: register.py.bak-nov23.
- Read-only Twilio check: no Holly profile or brand exists yet; 517-300-8226 is still on Manitou's service MG286.
- Board row "Holly: move 517-300-8226 off Manitou's A2P campaign" updated and set to Today. Session Brain row written.

**What's live / deployed:**
- Nothing submitted to Twilio. No site changes.

**Next up:**
- Yeti: `ssh root@143.198.171.9`, `cd /root/holly-a2p && python3 register.py brand`, type the federal EIN at the hidden prompt (brand fee applies), then `python3 register.py status` about ten minutes later.
- Campaign step stays blocked on Holly reviewing the privacy/terms branch (holly-privacy-sms-consent, efa8410) and on her brokerage decision due about Nov 24: campaign.py names Foundation Realty in the description, two sample texts and the HELP reply.

**Notes for other environments:**
- The EIN is not stored anywhere by design. Twilio matches the name against the IRS CP 575; if identity comes back unverified, the appeal needs the federal letter from her accountant, a state document will not do.