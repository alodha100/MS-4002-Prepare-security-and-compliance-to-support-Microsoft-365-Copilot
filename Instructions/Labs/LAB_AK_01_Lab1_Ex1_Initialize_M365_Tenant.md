---
lab:
  title: Learning Path 1 - Lab 1 - Exercise 1 - Initialize your Microsoft 365 Tenant
  description: 'Sign in to your Microsoft 365 trial tenant, create a pilot group and theme, and install Microsoft Graph PowerShell.'
  duration: 5 minutes
  level: 300
  islab: true
  primarytopics:
    - Microsoft 365
---

# Initialize your Microsoft 365 tenant

In this exercise, you’ll prepare Adatum’s Microsoft 365 trial tenant for the labs that follow. You’ll sign in as the tenant administrator, create a pilot team and custom theme, and install Microsoft Graph PowerShell.

## At a glance

| Task | What you’ll do |
|---|---|
| 1. Sign in | Open the Microsoft 365 admin center as **MOD Administrator** |
| 2. Create a pilot theme | Create the **M365 pilot project** group and configure a group theme |
| 3. Install Graph PowerShell | Install the module and verify the components used in later labs |

### Before you begin

You need the lab-hosting provider’s VM environment and the credentials below. Start on **LON-CL1**.

| Account | Use | Initial password |
|---|---|---|
| `Adatum\Administrator` | Sign in to the **LON-CL1** VM | `Pa55w.rd` |
| MOD Administrator (`admin@xxxxxZZZZZZ.onmicrosoft.com`) | Sign in to Microsoft 365 | **Administrative Password** |

Replace `xxxxxZZZZZZ` with the tenant prefix provided by your lab host. Your host may supply a new administrative password and a new user password; use them when prompted and keep them available for later labs.
The **Administrative Password** is for MOD Administrator. The **User Password** is for all other predefined users, including users assigned an admin role.

> [!NOTE]
> All predefined tenant users must change their password at first sign-in. If your lab host provides **New Administrative Password** and **New User Password** fields, use the new administrative password for MOD Administrator and Holly Dickson, and the new user password for other users. If these fields aren’t available, record the new passwords you choose. Passwords must be at least eight characters and include an uppercase letter, a lowercase letter, and a special character. Microsoft checks these requirements when the password is changed.

> [!WARNING]
> These trial tenants are for the course’s hands-on labs only. Do not share the tenant, use it for other purposes, or convert it to a paid subscription. The tenant remains Microsoft’s property, may be repossessed at any time, and cannot be accessed or extended after the class.

## Task 1: Sign in to the Microsoft 365 admin center

You’ll role-play as **Holly Dickson**, Adatum’s Microsoft 365 administrator. For this exercise, sign in with the provider-created **MOD Administrator** account. Holly’s personal account is created in the next exercise.

1. If your VM opens on a computer other than **LON-CL1**, switch to **LON-CL1**.
2. Sign in to Windows as **Administrator** using the password provided by your lab host.
3. Open **Microsoft Edge** and go to [Microsoft 365](https://portal.office.com).
4. Enter the **Administrative Username** provided by your host. It should look like `admin@xxxxxZZZZZZ.onmicrosoft.com`. Select **Next**.

   > [!TIP]
   > If your lab instructions provide a **Type text** button or another copy-and-paste option for usernames, passwords, or commands, use it to avoid typing errors.

5. Enter the **Administrative Password** and select **Sign in**.
6. If prompted to update the password, enter the initial **Administrative Password** as the current password, then enter and confirm your **New Administrative Password**.
7. If **Stay signed in?** appears, select **Don’t show this again**, then select **Yes**.
8. Dismiss any first-run messages:
   - On the **Welcome to Microsoft 365** slides, select the forward arrow twice, then select the check mark.
   - Close **Find more apps** or **Create with Microsoft 365** with **X**.
   - If prompted to sign in to Edge, select **No thanks**.
9. On the Microsoft 365 home page, select **Admin** in the navigation pane to open the admin center in a new tab.
10. In the admin center, select **Show all** in the navigation pane.

Leave the admin center open on **LON-CL1** for the next task.

## Task 2: Create a pilot group and custom theme

Custom themes are assigned to Microsoft 365 groups. First, create a group for the pilot team; then create a theme for that group that displays each signed-in user’s name.

### Create the Microsoft 365 group

1. In the admin center, select **Teams & groups** > **Active teams & groups**.
2. On the **Teams & Microsoft 365 groups** tab, select **+ Add a Microsoft 365 group**.
3. On **Set up the basics**, enter:
   - **Name:** `M365 pilot project`
   - **Description:** `Members of the Microsoft 365 pilot project team`

   Select **Next**. If **Next** is unavailable, select the Description field.
4. Select **+ Assign owners**. Select **MOD Administrator**, then select **Add (1)**. Confirm the owner and select **Next**.
5. Select **+ Add members**. Select these 10 users, then select **Add (10)**:

   - Alex Wilber
   - Allan Deyoung
   - Diego Siciliani
   - Isaiah Langer
   - Joni Sherman
   - Lynne Robbins
   - Megan Bowen
   - MOD Administrator
   - Nestor Wilke
   - Patti Fernandez

   Confirm that all 10 users appear on the **Add members** page. Add any missing users, then select **Next**.
6. On **Edit settings**, set:
   - **Group email address:** `m365pilotproject`
   - **Privacy:** **Private**
   - **Create a team for this group:** Selected

   Select **Next**.
7. Review the group details. Use **Edit** to correct any section, then select **Create group**.
8. When the confirmation appears, select **Close**. The group may take up to five minutes to appear. On **Active teams & groups**, select **Refresh** until **M365 pilot project** is listed.

### Configure the group theme

1. In the admin center, select **Settings** > **Org settings** > **Organization profile** > **Custom themes**.
2. In **Customize Microsoft 365 for your organization**, select **+ Add theme**.
3. In the **New group theme** pane, on the **General** tab:
   - Enter **M365 pilot project theme** as the name.
   - Select the **Groups** field and choose **M365 pilot project**. If it isn’t listed, search for `M365` and select the group from the results.
   - Select **Show the user’s display name**.
4. Review the **Logos** and **Colors** tabs. You can leave the defaults or explore the branding options. If you change colors, avoid combinations that are difficult to read, such as bright pink on white.
5. Select **Save**.

   > [!IMPORTANT]
   > The admin center may show **“Sorry, we couldn't save your theme. Please try again later.”** This is a known platform issue. If it occurs, the theme won’t be applied, but it won’t affect later labs. Close the theme pane and skip the next step.

6. If the theme saved, refresh the page. The **MOD Administrator** display name should appear beside the account icon or initials. The theme will show names for members of the pilot group when they sign in.
7. Return to **Custom themes**. The list shows the **Default theme** and, if saved, **M365 pilot project theme**. Select **Default theme** and review **Show the user’s display name**.

   By default, **Show the user’s display name** is not selected for the Default theme. If the custom theme failed to save, select this option and select **Save** to see how the setting works for all users. Refresh the page to check for the MOD Administrator name.

8. Close the theme pane and leave the admin center open for the next task.

## Task 3: Install Microsoft Graph PowerShell

You’ll use Microsoft Graph PowerShell in later labs to perform Microsoft 365 administration tasks.

1. On **LON-CL1**, open an elevated PowerShell window: right-click **Start**, then select **Windows PowerShell (Admin)**. Maximize the window.
2. Run this command to install the module:

   ```powershell
   Install-Module Microsoft.Graph -Scope CurrentUser
   ```

3. If prompted to install from the untrusted **PSGallery** repository, enter **A** for **Yes to All**, then press **Enter**.

   > [!NOTE]
   > The submodule messages may finish before setup is complete. Allow another 5–10 minutes for the installation; the prompt will return when it’s done.

4. List the installed Graph modules:

   ```powershell
   Get-InstalledModule Microsoft.Graph.* | Select-Object Name
   ```

5. Verify that these three modules are listed:

   - `Microsoft.Graph.Groups`
   - `Microsoft.Graph.Identity.DirectoryManagement`
   - `Microsoft.Graph.Users`

   If any are missing, install each missing module:

   ```powershell
   Install-Module -Name <module name> -Scope CurrentUser
   ```

   For example:

   ```powershell
   Install-Module -Name Microsoft.Graph.Identity.DirectoryManagement -Scope CurrentUser
   ```

6. Set the execution policy:

   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

   If prompted to confirm the change, enter **A** for **Yes to All**.
7. Leave the PowerShell window open for the next task.

## Exercise complete

You’ve signed in to the tenant, prepared the pilot group and theme, and installed Microsoft Graph PowerShell. You’re ready to continue with the remaining lab exercises.

# End of Lab 1
