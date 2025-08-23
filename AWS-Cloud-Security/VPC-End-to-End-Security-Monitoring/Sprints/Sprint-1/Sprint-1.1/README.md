# Sprint 1.1: AWS Networking and Security Groups Setup for Juice Shop Security Monitoring

**Author:** Oluwaseun Osunsola

This document details the steps performed to configure the AWS networking infrastructure and security groups for the "End-to-End Security Monitoring with Suricata IPS, AWS CloudWatch & Splunk on OWASP Juice Shop" project during Sprint 1.1 (Day 1). The goal was to establish a VPC, subnets, an internet gateway, route tables, and security groups to support the deployment of the OWASP Juice Shop and Suricata IPS. Each step is linked to a screenshot for reference.

## Prerequisites
- AWS account with permissions to create VPCs, subnets, internet gateways, route tables, and security groups.
- Familiarity with the AWS Management Console.

## Resources Created
### Networking
- **VPC**: `JuiceShop-VPC` (CIDR: `10.0.0.0/16`)
- **Public Subnet**: `Public-Subnet` (CIDR: `10.0.1.0/24`)
- **Private Subnet**: `Private-Subnet` (CIDR: `10.0.2.0/24`)
- **Internet Gateway**: `JuiceShop-IGW` (attached to `JuiceShop-VPC`)
- **Public Route Table**: `JuiceShop-Public-RT` (routes: local + `0.0.0.0/0 → JuiceShop-IGW`)
- **Private Route Table**: `JuiceShop-Private-RT` (routes: local only)

### Security Groups
- **JuiceShop-WebSG** (for OWASP Juice Shop instance)
  - Inbound: HTTP (80), HTTPS (443) from `0.0.0.0/0`; SSH (22) from your IP
  - Outbound: Allow All
- **JuiceShop-IPS-SG** (for Suricata IPS instance)
  - Inbound: HTTP/HTTPS from `JuiceShop-WebSG`; SSH (22) from your IP
  - Outbound: Allow All

## Steps
# Sprint 1.1: AWS Networking and Security Groups Setup for Juice Shop Security Monitoring

**Author:** Oluwaseun Osunsola

This document details the steps performed to configure the AWS networking infrastructure and security groups for the "End-to-End Security Monitoring with Suricata IPS, AWS CloudWatch & Splunk on OWASP Juice Shop" project during Sprint 1.1 (Day 1). The goal was to establish a VPC, subnets, an internet gateway, route tables, and security groups to support the deployment of the OWASP Juice Shop and Suricata IPS. Each step is linked to a screenshot for reference.

## Prerequisites
- AWS account with permissions to create VPCs, subnets, internet gateways, route tables, and security groups.
- Familiarity with the AWS Management Console.

## Resources Created
### Networking
- **VPC**: `JuiceShop-VPC` (CIDR: `10.0.0.0/16`)
- **Public Subnet**: `Public-Subnet` (CIDR: `10.0.1.0/24`)
- **Private Subnet**: `Private-Subnet` (CIDR: `10.0.2.0/24`)
- **Internet Gateway**: `JuiceShop-IGW` (attached to `JuiceShop-VPC`)
- **Public Route Table**: `JuiceShop-Public-RT` (routes: local + `0.0.0.0/0 → JuiceShop-IGW`)
- **Private Route Table**: `JuiceShop-Private-RT` (routes: local only)

### Security Groups
- **JuiceShop-WebSG** (for OWASP Juice Shop instance)
  - Inbound: HTTP (80), HTTPS (443) from `0.0.0.0/0`; SSH (22) from your IP
  - Outbound: Allow All
- **JuiceShop-IPS-SG** (for Suricata IPS instance)
  - Inbound: Custom TCP (8080) from `JuiceShop-WebSG`; SSH (22) from your IP
  - Outbound: Allow All

## Steps

1. **Search for VPC in AWS Console**  
   Searched for "VPC" in the AWS Console's service search bar to access the VPC dashboard.  
   ![Search for VPC](../../../img/1.on_the_aws_console_use_service_search_bar.png)

2. **Click on VPC (Virtual Private Cloud)**  
   From the search results, clicked on "VPC" to access the VPC dashboard.  
   ![VPC Dashboard](../../../img/2.search_for_vpc(virtual_private_cloud)_and_click_on_it.png)

3. **Open VPC Dashboard → Create VPC**  
   Landed on the VPC dashboard and clicked "Create VPC" to start network setup.  
   ![Open VPC Dashboard](../../../img/3.landed_on_vpc_dashboard_click_create_vpc_to_create_vpc.png)

4. **Choose “VPC only”, add tag**  
   Selected "VPC only," named it `JuiceShop-VPC`, and added a tag.  
   ![Configure VPC](../../../img/4.under_resource_to_create_choose_vpc_only_give_it_a_tag_and_scroll_down.png)

5. **Set CIDR IPv4 and create VPC**  
   Set the IPv4 CIDR block to `10.0.0.0/16`, left other settings at default, and clicked "Create VPC."  
   ![Create VPC](../../../img/5.manually_set_cidr_ipv4_leave_every_other_things_at_default_and_click_create_vpc.png)

6. **VPC successfully created → Go to Subnets**  
   Verified that `JuiceShop-VPC` was created and navigated to the subnets page.  
   ![VPC Created](../../../img/6.vpc_succefully_created_click_on_subnets.png)

7. **On Subnets page, click Create Subnet**  
   On the subnets page, clicked "Create subnet" to define `Public-Subnet` and `Private-Subnet`.  
   ![Create Subnet](../../../img/7.on_subnets_page_click_create_subnet.png)

8. **Select JuiceShop-VPC for subnet creation**  
   Selected `JuiceShop-VPC` and proceeded to subnet settings.  
   ![Select VPC](../../../img/8.select_your_vpc_name(JuiceShop-VPC)_scroll_to_subnet_setting_to_add_public_subnet.png)

9. **Create Public + Private subnets**  
   Named the first subnet `Public-Subnet`, chose an Availability Zone, set CIDR to `10.0.1.0/24`, clicked "Add new subnet," then named the second subnet `Private-Subnet`, selected the same Availability Zone, and set CIDR to `10.0.2.0/24`.  
   ![Configure Subnets](../../../img/9.set_subnet_name_availability_zone_cidr_ipv4_and_click_add_new_subnet_to_add_private_subnet.png)

10. **Confirm Subnets creation**  
    Verified that `Public-Subnet` and `Private-Subnet` were successfully created.  
    ![Subnets Created](../../../img/10.set_subnet_name_availability_zone(same_zone)_cidr_ipv4_and_click_create_subnet.png)

11. **Subnet successfully created**  
    Confirmed the successful creation of subnets.  
    ![Subnet Confirmation](../../../img/11.subnet_successfully_created.png)

12. **On VPC page, click Internet Gateways**  
    On the `JuiceShop-VPC` page, clicked "Internet Gateways" to create `JuiceShop-IGW`.  
    ![Internet Gateways](../../../img/12.on_JuiceShop-VPC_page_click_internet_gateways.png)

13. **Click Create Internet Gateway**  
    Landed on the Internet Gateway page and clicked "Create internet gateway."  
    ![Create IGW](../../../img/13.landed_on_internet_gateway_page_click_create_internet_gateway.png)

14. **Name it JuiceShop-IGW and create**  
    Named it `JuiceShop-IGW` and clicked "Create internet gateway."  
    ![Name IGW](../../../img/14.named_it_JuiceShop-IGW_and_clicked_create_internet_gate_way.png)

15. **IGW created → Click Attach to VPC**  
    Verified that `JuiceShop-IGW` was created and clicked "Attach to a VPC."  
    ![IGW Created](../../../img/15.IGW_succeessfully_created_click_attach_to_a_vpc.png)

16. **Select JuiceShop-VPC and attach**  
    Selected `JuiceShop-VPC` and attached `JuiceShop-IGW`.  
    ![Attach IGW](../../../img/16.selected_JuiceShop-Vpc_and_click_attach_to_internet_gate_way.png)

17. **IGW successfully attached**  
    Verified that `JuiceShop-IGW` was successfully attached to `JuiceShop-VPC`.  
    ![IGW Attached](../../../img/17.internet_gateway_successfully_attached_to_vpc.png)

18. **Click on Route Tables**  
    Clicked "Route Tables" to configure `JuiceShop-Public-RT` and `JuiceShop-Private-RT`.  
    ![Route Tables](../../../img/18.click_on_route_tables.png)

19. **On Route Tables page → Create route table**  
    On the route table page, clicked "Create route table."  
    ![Create Route Table](../../../img/19.on_route_table_page_click_create_route_table.png)

20. **Name it JuiceShop-Public-RT**  
    Named it `JuiceShop-Public-RT`, selected `JuiceShop-VPC`, and created the route table.  
    ![Public Route Table](../../../img/20.name_Public-RT_select_JuiceShop-VPC_and_create_route_table.png)

21. **Public RT created → Click Associate Subnet**  
    Noted the default local route (`10.0.0.0/16`) and clicked "Associate subnet" to link `Public-Subnet`.  
    ![Associate Subnet](../../../img/21.successfully_created_note_default_local_route_allow_public_subnet_talk_to_others_inside_the_vpc_click_on_associate_subnet.png)

22. **Click Edit Subnet Associations**  
    Clicked "Edit subnet associations" to proceed.  
    ![Edit Associations](../../../img/22.click_edit_subnet_associations.png)

23. **Select Public Subnet and save**  
    Selected `Public-Subnet` and saved the association.  
    ![Select Subnet](../../../img/23.select_Public-Subnet_and_click_save_association.png)

24. **Association successful**  
    Verified that the association was successful.  
    ![Association Successful](../../../img/24.association_successful.png)

25. **Click Edit Route for Public RT**  
    Clicked "Edit routes" to add an internet route for `JuiceShop-Public-RT`.  
    ![Edit Routes](../../../img/25.click_on_edit_route.png)

26. **Add new route ignoring default**  
    Ignored the default local route and clicked "Add route."  
    ![Add Route](../../../img/26.click_on_add_route_ignoring_the_default_route.png)

27. **Set destination 0.0.0.0/0 → JuiceShop-IGW**  
    Set the destination to `0.0.0.0/0`, selected `JuiceShop-IGW`, and saved changes.  
    ![Set Route](../../../img/27.set_destination_ip_select_internet_gateway_and_choose_JuiceShop-IGW_and_save_changes.png)

28. **Route update successful**  
    Verified that the route update for `JuiceShop-Public-RT` was successful.  
    ![Route Updated](../../../img/28.route_update_successful.png)

29. **Back to Route Tables → Create Private RT**  
    Navigated back to route tables to create `JuiceShop-Private-RT`.  
    ![Create Private RT](../../../img/29.click_on_route_tables_to_create_private_route_table.png)

30. **Click Create Route Table**  
    On the route table page, clicked "Create route table."  
    ![Create Route Table](../../../img/30.on_route_table_page_click_create_route_table.png)

31. **Name it JuiceShop-Private-RT**  
    Named it `JuiceShop-Private-RT`, selected `JuiceShop-VPC`, and created the route table.  
    ![Private Route Table](../../../img/31.named_Private-RT_and_selected_JuiceShop-VPC_and_created_route_table.png)

32. **Private RT created → Associate Subnet**  
    Noted the default local route and clicked "Associate subnet" to link `Private-Subnet`.  
    ![Associate Subnet](../../../img/32.successfully_created_note_default_local_route_allow_private_subnet_talk_to_others_inside_the_vpc_click_on_associate_subnet.png)

33. **Click Edit Subnet Associations**  
    Clicked "Edit subnet associations" to proceed.  
    ![Edit Associations](../../../img/33.click_edit_subnet_associations.png)

34. **Select Private Subnet and save**  
    Selected `Private-Subnet` and saved the association.  
    ![Select Subnet](../../../img/34.select_Private-Subnet_and_click_save_association.png)

35. **Association successful → Back to VPC**  
    Verified that the association was successful and navigated back to the VPC dashboard.  
    ![Association Successful](../../../img/35.association_successful_navigate_back_to_vpc.png)

36. **Click on Security Groups**  
    Clicked "Security Groups" to configure access rules for `JuiceShop-WebSG` and `JuiceShop-IPS-SG`.  
    ![Security Groups](../../../img/36.click_on_security_group.png)

37. **Ignore default → Create Security Group**  
    Ignored the default security group and clicked "Create security group."  
    ![Create Security Group](../../../img/37.ignore_default_and_click_on_create_security_group.png)

38. **Name it JuiceShop-WebSG and add description**  
    Named it `JuiceShop-WebSG`, added a description, selected `JuiceShop-VPC`, and proceeded to configure rules.  
    ![Configure WebSG](../../../img/38.named_it_JuiceShop-WebSG_add_description_and_select_JuiceShop-VPC_and_scroll_down.png)

39. **Add inbound rules HTTP/SSH → Create SG**  
    Added HTTP (80) and HTTPS (443) from `0.0.0.0/0`, SSH (22) from your IP, left outbound as "Allow All," and created the security group.  
    ![Inbound Rules](../../../img/39.under_inbound_rule_click_add_rule_and_add_http_(anywhere)_and_ssh(only_my_pc)_leave_outbound_and_create_security_group.png)

40. **WebSG created successfully**  
    Verified that `JuiceShop-WebSG` was successfully created.  
    ![WebSG Created](../../../img/40.security_group_successfully_created.png)

41. **Click on VPC**  
    Clicked "VPC" to continue configuring security groups.  
    ![VPC Dashboard](../../../img/41.click_on_vpc.png)

42. **Click on Security Groups again**  
    Clicked "Security Groups" to create `JuiceShop-IPS-SG`.  
    ![Security Groups](../../../img/42.click_on_security_group.png)

43. **Note WebSG in list → Create SG**  
    Noted that `JuiceShop-WebSG` appeared in the list and clicked "Create security group" for Suricata.  
    ![WebSG Listed](../../../img/43.note_JuiceShop-WebSG_is_now_in_the_list_click_create_security_group.png)

44. **Name it JuiceShop-IPS-SG and add description**  
    Named it `JuiceShop-IPS-SG`, added a description, selected `JuiceShop-VPC`, and proceeded to configure rules.  
    ![Configure IPS-SG](../../../img/44.named_it_JuiceShop-IPS-SG_add_description_and_select_JuiceShop-VPC_and_scroll_down.png)

45. **Add inbound rule (custom TCP 8080 from WebSG)**  
    Added Custom TCP (8080) with the source set to `JuiceShop-WebSG`, SSH (22) from your IP, set outbound to "Allow All," and created the security group.  
    ![IPS-SG Rules](../../../img/45.set_custom_tcp_port_to_8080_custom_source_Security_Group_JuiceShop-WebSG_and_click_create_security_group.png)

46. **IPS-SG created successfully**  
    Verified that `JuiceShop-IPS-SG` was successfully created.  
    ![IPS-SG Created](../../../img/46.security_group_successfully_created.png)

47. **Click on Security Groups to confirm**  
    Clicked "Security Groups" to confirm the creation of `JuiceShop-IPS-SG`.  
    ![Confirm Creation](../../../img/47.click_on_security_group_to_confirm_creation_of_security_group.png)

    ![](../../../img/

48. **Verify both SGs exist**  
    Confirmed that both `JuiceShop-WebSG` and `JuiceShop-IPS-SG` were listed.  
    ![Both Security Groups](../../../img/48.note_both_security_groups.png)

## Outcome
The AWS networking infrastructure and security groups were successfully configured:
- **VPC**: `JuiceShop-VPC` with CIDR `10.0.0.0/16`.
- **Subnets**: `Public-Subnet` (`10.0.1.0/24`) and `Private-Subnet` (`10.0.2.0/24`).
- **Internet Gateway**: `JuiceShop-IGW` attached to `JuiceShop-VPC`.
- **Route Tables**:
  - `JuiceShop-Public-RT`: Routes local traffic and `0.0.0.0/0` to `JuiceShop-IGW`, associated with `Public-Subnet`.
  - `JuiceShop-Private-RT`: Routes local traffic only, associated with `Private-Subnet`.
- **Security Groups**:
  - `JuiceShop-WebSG`: Allows HTTP (80), HTTPS (443) from anywhere, SSH (22) from your IP.
  - `JuiceShop-IPS-SG`: Allows Custom TCP (8080) from `JuiceShop-WebSG`, SSH (22) from your IP.

This setup provides a secure and isolated network environment for deploying the OWASP Juice Shop and Suricata IPS in subsequent sprints.
1. **Navigate to VPC Dashboard**  
   Searched for "VPC" in the AWS Console's service search bar to access the VPC dashboard.  
   ![Search for VPC](../../../img/1.on_the_aws_console_use_service_search_bar.png)

2. **Access VPC Creation Page**  
   From the VPC dashboard, clicked "Create VPC" to begin network setup.  
   ![VPC Dashboard](../../../img/2.search_for_vpc(virtual_private_cloud)_and_click_on_it.png)

3. **Create VPC**  
   Selected "VPC only," named it `JuiceShop-VPC`, set the IPv4 CIDR block to `10.0.0.0/16`, and left other settings at default. Clicked "Create VPC."  
   ![Configure VPC](../../../img/4.under_resource_to_create_choose_vpc_only_give_it_a_tag_and_scroll_down.png)

4. **Confirm VPC Creation**  
   Verified that `JuiceShop-VPC` was successfully created. Navigated to the subnets page.  
   ![VPC Created](../../../img/5.manually_set_cidr_ipv4_leave_every_other_things_at_default_and_click_create_vpc.png)

5. **Access Subnet Creation**  
   On the subnets page, clicked "Create subnet" to define `Public-Subnet` and `Private-Subnet`.  
   ![Subnets Page](../../../img/6.vpc_succefully_created_click_on_subnets.png)

6. **Select VPC for Subnets**  
   Selected `JuiceShop-VPC` and proceeded to subnet settings to add `Public-Subnet`.  
   ![Select VPC](../../../img/7.on_subnets_page_click_create_subnet.png)

7. **Configure Public Subnet**  
   Named the subnet `Public-Subnet`, chose an Availability Zone, set the CIDR block to `10.0.1.0/24`, and clicked "Add new subnet" to configure `Private-Subnet`.  
   ![Public Subnet Settings](../../../img/8.select_your_vpc_name(JuiceShop-VPC)_scroll_to_subnet_setting_to_add_public_subnet.png)

8. **Configure Private Subnet**  
   Named the subnet `Private-Subnet`, selected the same Availability Zone, set the CIDR block to `10.0.2.0/24`, and clicked "Create subnet."  
   ![Private Subnet Settings](../../../img/9.set_subnet_name_availability_zone_cidr_ipv4_and_click_add_new_subnet_to_add_private_subnet.png)

9. **Confirm Subnet Creation**  
   Verified that `Public-Subnet` and `Private-Subnet` were successfully created.  
   ![Subnets Created](../../../img/10.set_subnet_name_availability_zone(same_zone)_cidr_ipv4_and_click_create_subnet.png)

10. **Navigate to Internet Gateway**  
    On the `JuiceShop-VPC` page, clicked "Internet Gateways" to create `JuiceShop-IGW`.  
    ![Internet Gateways](../../../img/11.subnet_successfully_created.png)

11. **Create Internet Gateway**  
    Landed on the Internet Gateway page and clicked "Create internet gateway."  
    ![Create IGW](../../../img/12.on_JuiceShop-VPC_page_click_internet_gateways.png)

12. **Configure Internet Gateway**  
    Named it `JuiceShop-IGW` and clicked "Create internet gateway."  
    ![Name IGW](../../../img/13.landed_on_internet_gateway_page_click_create_internet_gateway.png)

13. **Confirm Internet Gateway Creation**  
    Verified that `JuiceShop-IGW` was created and clicked "Attach to a VPC."  
    ![IGW Created](../../../img/14.named_it_JuiceShop-IGW_and_clicked_create_internet_gate_way.png)

14. **Attach Internet Gateway to VPC**  
    Selected `JuiceShop-VPC` and attached `JuiceShop-IGW`.  
    ![Attach IGW](../../../img/15.IGW_succeessfully_created_click_attach_to_a_vpc.png)

15. **Confirm Internet Gateway Attachment**  
    Verified that `JuiceShop-IGW` was successfully attached to `JuiceShop-VPC`.  
    ![IGW Attached](../../../img/16.selected_JuiceShop-Vpc_and_click_attach_to_internet_gate_way.png)

16. **Navigate to Route Tables**  
    Clicked "Route Tables" to configure `JuiceShop-Public-RT` and `JuiceShop-Private-RT`.  
    ![Route Tables](../../../img/17.internet_gateway_successfully_attached_to_vpc.png)

17. **Create Public Route Table**  
    On the route table page, clicked "Create route table."  
    ![Create Route Table](../../../img/18.click_on_route_tables.png)

18. **Configure Public Route Table**  
    Named it `JuiceShop-Public-RT`, selected `JuiceShop-VPC`, and created the route table.  
    ![Public Route Table](../../../img/19.on_route_table_page_click_create_route_table.png)

19. **Associate Public Subnet**  
    Noted the default local route (`10.0.0.0/16`) allowing communication within `JuiceShop-VPC`. Clicked "Associate subnet" to link `Public-Subnet`.  
    ![Associate Subnet](../../../img/20.name_Public-RT_select_JuiceShop-VPC_and_create_route_table.png)

20. **Edit Subnet Associations**  
    Clicked "Edit subnet associations" to proceed.  
    ![Edit Associations](../../../img/21.successfully_created_note_default_local_route_allow_public_subnet_talk_to_others_inside_the_vpc_click_on_associate_subnet.png)

21. **Select Public Subnet**  
    Selected `Public-Subnet` and saved the association.  
    ![Select Subnet](../../../img/22.click_edit_subnet_associations.png)

22. **Confirm Public Subnet Association**  
    Verified that the association was successful.  
    ![Association Successful](../../../img/23.select_Public-Subnet_and_click_save_association.png)

23. **Edit Public Route Table**  
    Clicked "Edit routes" to add an internet route for `JuiceShop-Public-RT`.  
    ![Edit Routes](../../../img/24.association_successful.png)

24. **Add Internet Route**  
    Ignored the default local route, added a route with destination `0.0.0.0/0`, selected `JuiceShop-IGW`, and saved changes.  
    ![Add Route](../../../img/25.click_on_edit_route.png)

25. **Confirm Route Update**  
    Verified that the route update for `JuiceShop-Public-RT` was successful.  
    ![Route Updated](../../../img/26.click_on_add_route_ignoring_the_default_route.png)

26. **Create Private Route Table**  
    Navigated back to route tables to create `JuiceShop-Private-RT`.  
    ![Route Tables](../../../img/27.set_destination_ip_select_internet_gateway_and_choose_JuiceShop-IGW_and_save_changes.png)

27. **Configure Private Route Table**  
    Named it `JuiceShop-Private-RT`, selected `JuiceShop-VPC`, and created the route table.  
    ![Private Route Table](../../../img/28.route_update_successful.png)

28. **Associate Private Subnet**  
    Noted the default local route for VPC communication. Clicked "Associate subnet" to link `Private-Subnet`.  
    ![Associate Subnet](../../../img/29.click_on_route_tables_to_create_private_route_table.png)

29. **Edit Private Subnet Associations**  
    Clicked "Edit subnet associations" to proceed.  
    ![Edit Associations](../../../img/30.on_route_table_page_click_create_route_table.png)

30. **Select Private Subnet**  
    Selected `Private-Subnet` and saved the association.  
    ![Select Subnet](../../../img/31.named_Private-RT_and_selected_JuiceShop-VPC_and_created_route_table.png)

31. **Confirm Private Subnet Association**  
    Verified that the association was successful and navigated back to the VPC dashboard.  
    ![Association Successful](../../../img/32.successfully_created_note_default_local_route_allow_private_subnet_talk_to_others_inside_the_vpc_click_on_associate_subnet.png)

32. **Navigate to Security Groups**  
    Clicked "Security Groups" to configure access rules for `JuiceShop-WebSG` and `JuiceShop-IPS-SG`.  
    ![Security Groups](../../../img/33.click_edit_subnet_associations.png)

33. **Create Security Group for Juice Shop**  
    Ignored the default security group and clicked "Create security group."  
    ![Create Security Group](../../../img/34.select_Private-Subnet_and_click_save_association.png)

34. **Configure Juice Shop Security Group**  
    Named it `JuiceShop-WebSG`, added a description, selected `JuiceShop-VPC`, and proceeded to configure rules.  
    ![Configure WebSG](../../../img/35.association_successful_navigate_back_to_vpc.png)

35. **Add Inbound Rules for Juice Shop**  
    Added HTTP (80) and HTTPS (443) from `0.0.0.0/0`, and SSH (22) from your IP. Left outbound rules as "Allow All" and created the security group.  
    ![Inbound Rules](../../../img/36.click_on_security_group.png)

36. **Confirm Juice Shop Security Group Creation**  
    Verified that `JuiceShop-WebSG` was successfully created.  
    ![WebSG Created](../../../img/37.ignore_default_and_click_on_create_security_group.png)

37. **Navigate to VPC Dashboard**  
    Clicked "VPC" to continue configuring security groups.  
    ![VPC Dashboard](../../../img/38.named_it_JuiceShop-WebSG_add_description_and_select_JuiceShop-VPC_and_scroll_down.png)

38. **Access Security Groups Again**  
    Clicked "Security Groups" to create `JuiceShop-IPS-SG`.  
    ![Security Groups](../../../img/39.under_inbound_rule_click_add_rule_and_add_http_(anywhere)_and_ssh(only_my_pc)_leave_outbound_and_create_security_group.png)

39. **Confirm Juice Shop Security Group in List**  
    Noted that `JuiceShop-WebSG` appeared in the list and clicked "Create security group" for Suricata.  
    ![WebSG Listed](../../../img/40.security_group_successfully_created.png)

40. **Configure Suricata Security Group**  
    Named it `JuiceShop-IPS-SG`, added a description, selected `JuiceShop-VPC`, and proceeded to configure rules.  
    ![Configure IPS-SG](../../../img/41.click_on_vpc.png)

41. **Add Inbound Rules for Suricata**  
    Added HTTP (80) and HTTPS (443) with the source set to `JuiceShop-WebSG`, and SSH (22) from your IP. Set outbound to "Allow All" and created the security group.  
    ![IPS-SG Rules](../../../img/42.click_on_security_group.png)

42. **Confirm Suricata Security Group Creation**  
    Verified that `JuiceShop-IPS-SG` was successfully created.  
    ![IPS-SG Created](../../../img/43.note_JuiceShop-WebSG_is_now_in_the_list_click_create_security_group.png)

43. **Verify All Security Groups**  
    Confirmed that both `JuiceShop-WebSG` and `JuiceShop-IPS-SG` were listed.  
    ![Both Security Groups](../../../img/44.named_it_JuiceShop-IPS-SG_add_description_and_select_JuiceShop-VPC_and_scroll_down.png)

## Outcome
The AWS networking infrastructure and security groups were successfully configured:
- **VPC**: `JuiceShop-VPC` with CIDR `10.0.0.0/16`.
- **Subnets**: `Public-Subnet` (`10.0.1.0/24`) and `Private-Subnet` (`10.0.2.0/24`).
- **Internet Gateway**: `JuiceShop-IGW` attached to `JuiceShop-VPC`.
- **Route Tables**:
  - `JuiceShop-Public-RT`: Routes local traffic and `0.0.0.0/0` to `JuiceShop-IGW`, associated with `Public-Subnet`.
  - `JuiceShop-Private-RT`: Routes local traffic only, associated with `Private-Subnet`.
- **Security Groups**:
  - `JuiceShop-WebSG`: Allows HTTP (80), HTTPS (443) from anywhere, SSH (22) from your IP.
  - `JuiceShop-IPS-SG`: Allows HTTP/HTTPS from `JuiceShop-WebSG`, SSH (22) from your IP.

This setup provides a secure and isolated network environment for deploying the OWASP Juice Shop and Suricata IPS in subsequent sprints.