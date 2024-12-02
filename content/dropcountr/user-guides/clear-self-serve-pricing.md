+++
title = 'CLEAR Self-Serve Pricing'
weight = 3
+++

# Introduction to Self-Serve Pricing

The CLEAR self-service pricing module allows utility employees to update pricing in CLEAR. This helps consumers more accurately estimate their water bill and receive notifications based on when their estimated bill reaches a threshold.

## Navigate to the Pricing Module

1. Log in to the [Dropcountr CLEAR dashboard](https://dropcountr.com/clear).
2. On the left menu bar, click **Pricings**. 
3. Click a pricing option to view existing pricing. The updated view allows you to see each version of pricing information separately. 
4. Click the **Expand** (+) button to view an expanded list showing the current pricing information and all historical versions.

![Navigate to the Pricing module](/images/pricing-navigation-1.png)

![View each version of Pricing separately](/images/pricing-navigation-2.png)

![Click the Expand button to view an expanded list of current pricing information and all historical versions](/images/pricing-navigation-3.png)

## Adding a New Pricing

To add a new pricing, follow the steps below:

1. Click the **\+Add** button. A menu will appear on the right side of the screen.
2. Enter a unique **Name** and **Import Code** in the open right panel. The import code must match the pricing ID  sent with service connection files or fetched from the smart meter’s API.
3. Select the appropriate **Billing Unit**.
4. Select the appropriate **Billing Period**. The billing period should be the frequency at which your utility sends out bills. 

**Note**: Consumers will see usage graphs displaying the billing unit. If the billing unit is not set to gallons, usage will be shown in that unit in addition to gallons.

![Add a new pricing](/images/add-new-pricing-1.png)

![Define Name, Import Code, and select appropriate Billing Unit and Billing Period](/images/add-new-pricing-2.png)

### Adding Fixed Charges

1. Click **Add Charge** in the Fixed Charges section to insert rows for fixed charges, such as meter and wastewater fees.
2. Click the trash icon under the **Action** column to delete the row if needed.

![Adding fixed charges](/images/add-fixed-charges.png)

### Adding Volumetric Tiers

1. Select the **Volumetric** option in the Tiers section.  
2. Click **Add Tier** to insert rows for each pricing tier.  
3. Click the trash icon under the **Action** column to delete the row if needed.

![Adding volumetric tiers](/images/add-volumetric-tiers.png)

### Adding Budget-Based Tiers

**Note**: Any information you have entered will not be saved if you switch between volumetric and budget-based.

1. Select the **Budget-Based** radio button in the **Tiers** section. This will create three default tiers based on common setups: 1 indoor budget, 1 outdoor budget, and anything above.  
2. Click **Add Tier** to insert rows for each pricing tier.  
3. Click the trash icon under the **Action** column to delete the row if needed.

**Note:** You must have at least two budget-based tiers, including the **anything above** tier.

![Adding budget-based tiers](/images/add-budget-based-tiers.png)

## Fallback Pricing

When utilities send KUBRA their list of service connections, each connection should include the associated pricing code. If a pricing code is not present, KUBRA will use the fallback pricing code. We recommend adding one with the **Import Code** set to _fallback_ to account for any service connections without an associated pricing code.

![Fallback pricing](/images/fallback-pricing.png)

## Editing Name, Import Code, and Billing Unit

Some pricing information, such as name, import code, billing unit, and billing period, are shared across all time intervals of a pricing. Follow the steps below to modify this information:

1. Select the relevant pricing from the list.  
2. Click the **Edit** button on the top right of the screen. The right panel will display the editor for these fields.

![Editing pricing information](/images/edit-pricing-1.png)

![Editing Name, Import Code, and Billing Unit](/images/edit-pricing-2.png)

## Editing Tiers

Follow the steps below to edit tiers:

1. Select the charge you wish to edit. Charges are shown when a pricing item is expanded in the menu list.   
2. Click the **Edit** button on the top right side of the screen.

![Navigating to editing tiers](/images/edit-tiers-1.png)

![Editing tiers](/images/edit-tiers-2.png)

## Adding Updated Pricing (Pricing History)

You can add updated pricing instead of updating the existing prices/values to maintain pricing history. There is currently only one charge in the following example pricing:

![Navigating to Pricing History](/images/add-updated-pricing-1.png)

Follow the steps below to add updated pricing:

1. Select the pricing that needs to be updated.  
2. Click the **Add Version** button at the top right of the screen to create a new set of charges. You can add the updated Fixed Fees and Tiers in the right panel.   
3. Select the **Effective From** date for the updated pricing.  
4. Click **Save** when you have added the updated pricing.

![Adding a new version](/images/add-updated-pricing-2.png)

![Saving the new version](/images/add-updated-pricing-3.png)

Once the new version is saved, the menu list will update automatically and show any additional or updated versions.

**Note**: The end date for the current charges will automatically be set to the effective date for the updated charges.

![Viewing the new version in the Pricing History](/images/add-updated-pricing-4.png)

![Details of the new version](/images/add-updated-pricing-5.png)

## Import Pricings

If you have a long list of pricings and would like to use a CSV file to import them to KUBRA Dropcountr, please contact KUBRA Support and inquire about file formatting and file transfer.
