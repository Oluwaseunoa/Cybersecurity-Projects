# Vulnerable Java Application Basic Application Security Testing
**Author:** Oluwaseun Osunsola  
**Environment:** Windows GUI and CLI   

**Project link:** https://github.com/Oluwaseunoa/Cybersecurity-Projects/tree/main/Static-Application-Security-Testing/SAST101-Vulnerable-Java-Application%20Test

## Executive Summary  
This project focuses on performing basic Static Application Security Testing (SAST) on a vulnerable Java application using SonarCloud as the primary analysis tool. The application source code was sourced from GitHub, and AWS CodeBuild was utilized to automate the build and scanning process. The goal was to identify security vulnerabilities in the Java code through automated scanning, demonstrating a simple DevSecOps pipeline integration.

Key tools and services used:    
- **SonarCloud**: For code quality and security analysis.    
- **GitHub**: As the repository source and version control system.    
- **AWS CodeBuild**: For building the project and integrating with SonarCloud.    

The project involved setting up a SonarCloud organization and project, generating access tokens, cloning and preparing the vulnerable Java repository, connecting GitHub to AWS, and running a build to trigger the SonarCloud scan. The results highlighted vulnerabilities in the code, providing insights for remediation.

## Project Structure
The project directory structure is as follows:

```
C:.
└───SAST101-Vulnerable-Java-Application Test
    ├───app
    │   └───.jdk
    │       └───bin
    ├───gradle
    │   └───wrapper
    ├───img
    └───src
        └───main
            └───java
```

This structure indicates a Gradle-based Java application, with source code in `src/main/java`, build tools in `gradle`, and an embedded JDK in `app/.jdk`. The `img` folder contains screenshots documenting the execution steps.

## Step-by-Step Execution  
The project was executed in a sequential manner, starting with SonarCloud setup, followed by repository preparation on GitHub, and concluding with AWS CodeBuild integration and scanning. Each step is described below, with references to the corresponding screenshot in the `img` folder. The screenshot filenames directly describe the actions taken.

1. **Navigate to SonarCloud Login Page**:   
Accessed the SonarCloud website to begin the setup process.  
   ![](./img/1.navigate_to_sonacloud_login_page.png)

2. **Sign In with GitHub**:   
Selected GitHub as the authentication method for SonarCloud login.  
   ![](./img/2.sign_in_with_any_option_i_choose_github.png)

3. **Create Organization at Welcome Screen**:   
On the welcome screen, clicked the plus icon to create a new organization.  
   ![](./img/3.at_the_welcome_screen_click_the_plus_icon_and_create_organization.png)

4. **Create Organization Manually**:   
At the organization creation page, opted to create one manually.  
   ![](./img/4.at_the_create_organization_page_click_create_one_manually.png)

5. **Choose Organization Name and Key**:  
Entered the organization name and key for identification.  
   ![](./img/5.choose_organization_name_and_key.png)

6. **Select Free Plan and Create Organization**:   
Chose the free plan and finalized organization creation.  
   ![](./img/6.select_free_plan_and_create_organization.png)

7. **Create Project in the Organization**:   
Within the newly created organization, initiated project creation.  
   ![](./img/7.in_the_succefully_created_organization_create_project.png)

8. **Create Project Manually**:   
Selected the manual option for project setup.  
   ![](./img/8.create_project_manually.png)

9. **Choose Display Name, Project Key, and Set to Public**:   
Specified the display name, project key, and set visibility to public.  
   ![](./img/9.choose_display_name_and_project_key_and_set_to_public.png)

10. **Select Previous Version and Click Create Project**:   
Chose the previous version option and created the project.  
    ![](./img/10.select_previous_version_and_click_create_project.png)

11. **Click on Account and My Account**:   
Accessed the account settings by clicking on the account menu and selecting "My Account".  
    ![](./img/11.click_on_account_and_my_account.png)

12. **Click on Security**:   
Navigated to the security section in account settings.  
    ![](./img/12.click_on_security.png)

13. **Enter Name, Generate Token, and Copy Generated Token**:   
Provided a name for the token, generated it, and copied the value.  
    ![](./img/13.enter_name_generate_token_and_copy_generated_token.png)

14. **Copy Generated Token (Not Visible Again)**:   
Noted and copied the token, as it would not be displayed again.  
    ![](./img/14.copy_generated_token_because_you_will_not_see_it_again.png)

15. **Locate Vulnerable Code Repository on GitHub and Copy HTTPS Link**:   
Found the vulnerable Java repository on GitHub and copied its HTTPS clone link.  
    ![](./img/15.locate_vulnerable_code_repository_on_github_and_copy_the_https_link.png)

16. **Navigate to Desired Location and Clone Repository**:   
Moved to the local directory and cloned the repository using the copied link.  
    ![](./img/16.navigate_to_the desired_location_and_clone_the_repository_using_the_copied_link.png)

17. **Create Project Folder**:   
Set up a new folder for the project.  
    ![](./img/17.create_project_folder.png)

18. **Copy Content of Cloned Repository into Project Folder**:   
Transferred the cloned repository contents into the new project folder.  
    ![](./img/18.copy_the_content_of_clone_repository_into_the_project_folder.png)

19. **Create Repository in the Name of Project Folder on GitHub**:   
Created a new GitHub repository matching the project folder name.  
    ![](./img/19.create_a_repository_in_the_name_of_project_folder_on_github.png)

20. **Copy Repository Link from Quick Setup Section**:   
Copied the new repository's link from the quick setup area.  
    ![](./img/20.copy_the_repository_link_on_the_quick_set_up_section.png)

21. **Initialize, Stage, Commit, and Push Repository to GitHub**:   
Initialized Git, staged files, committed changes, and pushed to the new GitHub repository.  
    ![](./img/21.initialize_stage_commit_and_push_repository_to_github.png)

22. **Reload GitHub to Confirm Upload**:   
Refreshed the GitHub page to verify the upload was successful.  
    ![](./img/22.reload_github_to_confirm_upload.png)

23. **Log In to AWS Console**:   
Accessed the AWS Management Console with credentials.  
    ![](./img/23.log_in_to_your_aws_console.png)

24. **Search for CodeBuild and Click on It**:   
Searched for "CodeBuild" in the AWS services and selected it.  
    ![](./img/24.search_for_codesbuild_and_click_on_it.png)

25. **Click on Create Project**:   
Initiated the creation of a new build project.  
    ![](./img/25.click_on_create_project.png)

26. **Name the Project and Scroll Downward**:   
Assigned a name to the project and proceeded downward.  
    ![](./img/26.name_the_project_and_scroll_downward.png)

27. **Select GitHub as Source Provider and Click on Manage Credentials**:  
Chose GitHub as the source and managed credentials.  
    ![](./img/27.select_GitHub_as_source_provider_and_click_on_manage_credentials.png)

28. **Click Create New GitHub Connection**:   
Started the process to create a new connection to GitHub.  
    ![](./img/28.click_create_new_github_connection.png)

29. **Create GitHub App Connection**:   
Set up the GitHub app connection.  
    ![](./img/29.create_github_app_connection.png)

30. **Click Connect to GitHub**:   
Connected the AWS account to GitHub.  
    ![](./img/30.click_connect_to_github.png)

31. **Click Install a New App**:   
Installed a new GitHub app for integration.  
    ![](./img/31.click_install_a_new_app.png)

32. **Click on GitHub Profile with Username**:   
Selected the GitHub profile associated with the account username.  
    ![](./img/32.click_on_the_github_profile_with_your_github_account_username.png)

33. **Authorize for All Repositories or Some**:   
Granted authorization for all or selected repositories.  
    ![](./img/33.authorize_for_all_repository_or_some.png)

34. **Authenticate with Device (If 2FA Enabled)**:   
Completed device authentication for two-factor setup.  
    ![](./img/34.authenticate_with_your_device_if_you_have_two_factor_authentication.png)

35. **Confirm Identity by Supplying Number Sent**:   
Entered the verification code sent for identity confirmation.  
    ![](./img/35.confirm_identity_by_supplying_number_sent_to_you.png)

36. **Click Connect After App Installation**:   
Finalized the connection post-installation.  
    ![](./img/36.connect_click_connect_after_app_installation.png)

37. **Select the New Connection**:   
Chose the newly created GitHub connection.  
    ![](./img/37.select_the_new_connection.png)

38. **Click Save**:   
Saved the connection settings.  
    ![](./img/38.click_save.png)

39. **Account Now Connected to GitHub**:   
Confirmed the successful connection between AWS and GitHub.  
    ![](./img/39.account_now_connected_to_github.png)

40. **Select from GitHub Repository and Choose Your Repository**:   
Picked the project repository from the GitHub sources.  
    ![](./img/40.selected_from_github_repository_and_select_your_repository.png)

41. **Leave Default OS Type and Spec**:   
Retained the default operating system type and specifications for the build environment.  
    ![](./img/41.leave_default_os_type_and_spec.png)

42. **Leave Default System and Runtime Under Environment**:   
Kept the default system and runtime settings in the environment configuration.  
    ![](./img/41.leave_default_sytem and_runtime_under_environment.png)  <!-- Note: Filename appears to have a typo in "system" -->

43. **Under Buildspec, Select Insert Build Command and Switch to Editor**:   
In the buildspec section, chose to insert commands and switched to the editor mode.  
    ![](./img/42.under_buildspec_select_insert_build_command_and_switch_to_editor.png)

44. **Paste Commands to the Text Editor**:   
Inserted the necessary build commands into the editor.  Find it [here](https://github.com/asecurityguru/aws-devsecops-repo-for-buildspec-with-sonarcloud-actualvalues/blob/main/buildspec.yml)
    ![](./img/43.paste_this_commands_to_the_text_editor.png)

45. **Fill in Organization, Project Key, and Token**:   
Entered the SonarCloud organization key, project key, and token into the configuration.  
    ![](./img/44.fill_in_your_organization_project_key_and_token.png)

46. **Click CloudWatch and Build Project**:   
Enabled CloudWatch logging and created the build project.  
    ![](./img/45.click_cloudwatch_and_build_project.png)

47. **Successfully Created Project Build**:   
Verified the successful creation of the build project.  
    ![](./img/46.succesfully_created_project_build.png)

48. **Start Build**:   
Initiated the build process.  
    ![](./img/47.start_build.png)

49. **Build Succeeded**:  
Confirmed the build completed successfully.  
    ![](./img/48.build_succeeded.png)

50. **Result Sent to Organization on SonarCloud**:   
Viewed the analysis results forwarded to the SonarCloud organization.  
    ![](./img/49.result_sent_to_my_organization_name_on_sonarcloud.png)

51. **Analysis Result on SonarCloud**:  
Reviewed the detailed vulnerability and code quality report on SonarCloud.  
    ![](./img/50.analysis_result_on_sonar_cloud.png)

## Results and Analysis  
The SonarCloud scan identified various vulnerabilities in the Java application, such as potential SQL injection risks, insecure dependencies, and code smells. The integration via AWS CodeBuild ensured automated scanning on code pushes, aligning with SAST best practices. Key metrics from the analysis included vulnerability counts, security hotspots, and code coverage suggestions.

## Conclusion and Recommendations  
This project successfully demonstrated a basic SAST pipeline for a vulnerable Java application using SonarCloud, GitHub, and AWS CodeBuild. Future enhancements could include integrating dynamic analysis tools, automating remediation workflows, or expanding to containerized builds. Regular scans are recommended to maintain application security. All steps were documented via screenshots for reproducibility.