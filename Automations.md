Automations provide a way for Business users to set up triggers, filters, and actions without having to use SQL code to build Rules. An Automation is a set of ordered Filter-Actions that is controlled by Triggers on a specific Trackor Type.  

Below are some of the key terms and capability of Automations:

- **Trigger Type** – Defines when or the type of Event in the system that will trigger the Automation. This is similar to the Rule Types in the platform. Currently, below Trigger types are supported:
  - Field Updated (After)
  - Task Date Updated (After)
  - Trackor Created (After)
  - Trackor Created/Updated (After)
  - Trackor Updated (After)
  - Trackor Deleted (Before)
- **Trackor Type** – Defines what type of records will be affected by the Automation. For instance, if Trigger Type is 'After Trackor Created' and Trackor Type is 'Job', the current Automation will get triggered every time a new Job record is created.
- **Stop on Filter Match** - This option allows an Automation to stop executing the ordered set of Filter-Actions, when a particular Filter-Action condition is met and executed, instead of processing the remaining Filter-Actions.
- **Enabled** - Entire Automation can be enabled or disabled with this checkbox.
- **Filter-Action**
  - **Filter** – Defines the actual records that will be affected by the Automation. Conditions that need to be validated for Automation’s Action to take place. This is similar to using a filter in a Trackor Browser grid. The Automation Filter can be used similar to setting a Grid Filter – the conditions in the Filter (Advanced Filter logic is also available) will have to be met (should evaluated to True) for a Trackor/record in order for the Automation Action to occur.
  - **Action:**
    - **Action** Type – Defines the type of Action that will be performed when Automation is triggered and validated. Currently ‘Field Update’, ‘Task Date Update’, 'Error Message', 'Field Lock-Unlock', and 'Field Set Color' are supported. For example, if the current Automation has an Action Type of 'Field Update', every time a Job record is created, a configured field will be updated
    - **Order Number** – Defines the order in which the Filter-Action will be executed within the Automation. A lower-order number means the Action will be executed earlier. When no order number is present it will be executed at the end. If multiple Filter-Actions exist with same order, execution order will be random.
    - **Enabled** - An action can be enabled/disabled for testing purposes
    - **Target Field** - The Field that will be updated in the Action.
    - **Action Mode** – A mechanism to set a 'Constant Value' or a value calculated by a 'Formula' or SQL code to a field. Currently, we support only one Action per Automation.
    - **Target Value** - The value that will be assigned to Target Field
    - **Formula, Trackor Types** - Formula can be used to enter PL/SQL code that can be used on selected Trackor Types. These fields are available when 'Formula' option is selected in Action Mode
- **Circular Dependency** - this tab in an Automation shows if there are any instances of circular dependencies between Automations which could cause an endless loop.
- **Automations tab in Configured Fields/Tasks** show a list of Automations where (Automation name) the current field/task is being used and how (Action/Filter/Trigger) it is being used.

Automation Grid
=

![](//port/image/automationGrid.png)

General Tab
-

An Automation is defined by a **Trackor Type** (to which it is associated), **Trigger Type** (action that triggers an Automation) and ordered set of **Filter-Actions**. Automation can now support **multiple Filter-Actions**  and we can enable an option to stop executing the ordered set of Filter-Actions when the first Filter condition has been met and its corresponding Action executed – this capability is called **'Stop on Filter Match'**.  In the screenshot below, since ‘Stop on Filter Match’ is enabled, the ordered set of Filter-Actions will stop after executing the Action, on the first Action ID whose Filter returns true. If ‘Stop on Filter Match’ is not enabled, all Action IDs will be evaluated – if Filter returns true, corresponding Action will be executed, dictated by the Order Number (ascending).