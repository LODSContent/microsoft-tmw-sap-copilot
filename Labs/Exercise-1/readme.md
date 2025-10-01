# Exercise 01: Create an SAP account and configure SAP resources

In this exercise, you'll create an SAP account. You'll also create an account so that you can access the SAP Gateway Demo system. The Gateway Demo system serves as the SAP data source for this lab.

## Objectives

After you complete this exercise, you'll be able to:

- Create an SAP account.
- Configure access to the SAP Gateway Demo system.

## Duration

**Estimated time**: 10-15 minutes

---

# Task 01: Create an SAP account

## Introduction

SAP controls access to demos and documentation. You need to create an account before you can access the SAP Gateway Demo system data.

## Description

In this task, you create an account so that you can access SAP resources.

## Success criteria

- You receive an email from SAP that includes the URI and credentials to access the SAP Gateway Demo system.
- You successfully connect to the AP Gateway Demo system.

## Learning resources

- [SAP Home page](https://www.sap.com/index.html "SAP Home page")

## Key tasks

1. [] Sign in to the @lab.VirtualMachine(WindowsDesktop).SelectLink virtual machine by using the following credentials:

   - Username: **Admin**
   - Password: +++@lab.VirtualMachine(WindowsDesktop).Password+++

2. [] Open Edge and go to `sap.com`.

3. [] At the upper right of the page, select the Sign in icon.

    ![The Sign in icon is displayed.](media/sap-sign-in-link.png)

    > [!NOTE]
    > If the **Sign in** icon is not visible, select the **&#9776;** icon to reveal the hidden options.

    ![The hidden options are displayed.](media/sap-sign-in-hamburger-menu.png)

4. [] In the **Login or create an SAP account** dialog, select **Create your SAP account**.

    ![The Create your SAP account link is displayed.](media/sap-create-account-link.png)

5. [] Enter the following information on the **Register** page of the **We see you're new to SAP** dialog:

	| box | Value |
	|:---------|:------|
    | First name| `Admin` |
    |Last name |`User`   |
    | Country/Region   | Select your country/region   |
    | Business e-mail address   | Enter your work or personal email address   |
    | Company  | `Contoso`   |
    | Department   | **Training**   |
    | Relationship to SAP  | **Student**   |

6. [] Select the **I have read and understood the Terms and Conditions of SAP.com** checkbox and then select **Submit**.

    ![The SAP account creation form is displayed.](media/sap-account-creation-form.png)

7. [] If prompted, complete the Captcha process.

8. [] Wait for the **Verify your e-mail** page of the **We see you're new to SAP** dialog to display.

    ![The Verify your e-mail page is displayed.](media/sap-verify-email.png)

9. [] Open your email app and go to the inbox. Locate an email from the sender **SAP Universal ID - Notification**.

    ![The email from SAP is displayed.](media/sap-account-verification-email.png)

10. [] Open the email. Locate the hyperlink below the **Click to activate your account** button.

    ![The SAP account activation link is displayed.](media/sap-account-activation-link.png)

11. [] Copy the link and then paste the link into the following textbox:

    SAP Account activation link: @lab.TextBox(SAPActivationLink)

    > [!WARNING]
    > After pasting the value into the text box, select the **Tab** key or any element outside of the text box. This ensures that the value is saved for use later in the lab.

12. [] Return to the lab environment. Open a new browser window and go to `@lab.Variable(SAPActivationLink)`.

13. [] In the **Finalize your account** dialog, enter the following values:

    - Password: `@lab.CloudPortalCredential(User1).Password`
    - Re-Enter Password: `@lab.CloudPortalCredential(User1).Password`

14. [] Select **Continue** through the remaining steps.

17. [] Close the **Welcome to your SAP.com account** dialog.

===

# Task 02: Create an account for the SAP Gateway Demo system

## Introduction

Now that you can access SAP resources, you must create an account to access demo data.

## Description

In this task, you sign in to the SAP developer site and create an account. The account provides access to the SAP Gateway Demo system.

## Success criteria

- You have valid credentials to use the SAP Gateway demo system

## Learning resources

- [Create an account on the SAP Gateway Demo system](https://developers.sap.com/tutorials/gateway-demo-signup..html "SAP Gateway Demo system")

## Key tasks

1. [] Open a new browser tab and go to `register.sapdevcenter.com/SUPSignForms/`.

1. [] On the **SAP Gateway Demo Server -ES5** page, copy the **User ID** value and paste it in the following text box:

    User ID: @lab.TextBox(ES5UserID)

1. [] Select the **I have read and understood the Terms and Conditions** checkbox, then select **Register**.

    ![The SAP Gateway Demo Server -ES5 registration form is displayed.](media/sap-gateway-demo-registration-form.png)

	>[!note] You'll see a page that says the registration is now being processed.

1. [] Select **Show password**. Paste the temporary password into the following text box:

    Temporary Password: @lab.TextBox(ES5TemPW)

    ![The temporary password is displayed.](media/sap-gateway-demo-temporary-password.png)

    > [!NOTE]
    > The SAP system will send you an email that includes the Server URI, username, and initial password.

1. [] Open a new browser tab and go to `https://sapes5.sapdevcenter.com/sap/bc/gui/sap/its/webgui`

1. [] On the **SAP NetWeaver** page, enter the following credentials, then then select **Log On**:

    | Item | Value |
    | ---- | ----- |
    | **User** | `@lab.Variable(ES5UserID)` |
    | **Password** | `@lab.Variable(ES5TemPW)` |

    ![The SAP NetWeaver login page is displayed.](media/sap-netweaver-login.png)

1. [] On the **SAP NetWeaver** page that displays, enter the following information to replace the temporary password and then select **Change**:

    | Item | Value |
    | ---- | ----- |
    | **Current Password** | `@lab.Variable(ES5TemPW)` |
    | **New Password** | `@lab.CloudPortalCredential(User1).Password` |
	| **Repeat Password** | `@lab.CloudPortalCredential(User1).Password` |

    ![The change password page is displayed.](media/sap-netweaver-change-password.png)

1. [] Verify the password was changed successfully, then select **Continue**.

    ![The password change success message is displayed.](media/sap-netweaver-password-change-success.png)

===

# Task 03: Save the SAP Gateway Demo API metadata

## Introduction

In this task, you download the SAP Gateway Demo API metadata file. The metadata file is used in later exercises to create an API connection to the SAP Gateway Demo system.

## Description

In this task, copy the SAP Gateway Demo API metadata, transform it into the OpenAPI format, and then save it to a file. This file is used in later exercises to create an API connection to the SAP Gateway Demo system.

## Success criteria

- You have a local copy of the SAP Gateway Demo API metadata file.

## Key tasks

1. [] Open a new browser tab and go to `sapes5.sapdevcenter.com/sap/opu/odata/iwbep/GWSAMPLE_BASIC/$metadata`. 

    >[!note] The SAP Gateway Demo API metadata displays in XML format:
	>
    >![The SAP Gateway Demo API metadata is displayed in XML format.](media/sap-gateway-demo-api-metadata-xml.png)

2. [] Select all text in the browser window and then copy it to the Windows clipboard.

3. [] Open a new browser tab and go to `convert.odata-openapi.net`.

1. [] Paste the XML text into the **Manual Input of OData Definition (XML)** text box.

    > [!WARNING]
    > If there is any non-XML text in the text box, delete it.
	![The OData to OpenAPI conversion tool with XML pasted is displayed.](media/odata-to-openapi-conversion-tool-xml-pasted.png)

6. [] Select the **Convert to OpenAPI3** button, then select **Download** to download the OpenAPI **openapi-spec.json** file.

    ![The OData to OpenAPI conversion tool with the Convert to OpenAPI3 button is displayed.](media/odata-to-openapi-conversion-tool-convert-button.png)
