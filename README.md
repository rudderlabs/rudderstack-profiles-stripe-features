# About
This is a Profiles library project to create user features from Stripe tables created using Rudderstack Extracts/ETL

# Inputs
## Raw Tables
| name | table | path |
| ---- | ----- | ---- |
| stripeCustomers | customers | analytics_db.data_apps_simulated_stripe.customers |
| stripeCharges | charges | analytics_db.data_apps_simulated_stripe.charges |
| stripeInvoices | invoices | analytics_db.data_apps_simulated_stripe.invoices |
| stripeBalanceHistory | balance_history | analytics_db.data_apps_simulated_stripe.balance_history |
| stripeSubscriptions | subscriptions | analytics_db.data_apps_simulated_stripe.subscriptions |
| stripeRefunds | refunds | analytics_db.data_apps_simulated_stripe.refunds |
| stripeInvoicesView | STG_INVOICES_DATA | ANALYTICS_DB.DATA_APPS_SIMULATED_STRIPE.STG_INVOICES_DATA |
# Identity Stitching
## user identities
| name | exclusions | sourced_from |
| ---- | ---------- | ------------ |
| balance_transaction_id | NaN | ["stripeCharges:balance_transaction","stripeBalanceHistory:id","stripeRefunds:balance_transaction"] |
| charge_id | NaN | ["stripeCharges:charges_id","stripeRefunds:charge"] |
| customer_id |  | ["stripeCustomers:customers_id","stripeCharges:customer","stripeInvoices:customer","stripeSubscriptions:customer","stripeInvoicesView:customer"] |
| invoice_id | NaN | ["stripeCharges:invoice","stripeInvoices:invoices_id"] |
| main_id |  | [] |
| subscription_id | NaN | ["stripeSubscriptions:subscriptions_id"] |
# Features
## user features
| Feature | Computed From | Description |
| ------- | ------------- | ----------- |
| active_plan_intervals | stripeInvoicesView |  |
| amt_spent_in_past_365_days | stripeBalanceHistory |  |
| amt_spent_subscriptions | stripeInvoicesView |  |
| average_transaction_value | stripeBalanceHistory |  |
| average_transaction_value_in_past_365_days | stripeBalanceHistory |  |
| current_amount_due_subscriptions | stripeInvoicesView |  |
| customer_currency | stripeCharges |  |
| days_since_first_sale |  |  |
| days_since_first_subscription |  |  |
| days_since_last_purchase |  |  |
| distinct_plans_subscribed | stripeInvoicesView |  |
| fees_in_past_365_days | stripeBalanceHistory |  |
| has_credit_card | stripeCharges |  |
| highest_transaction_value | stripeBalanceHistory |  |
| highest_transaction_value_in_past_365_days | stripeBalanceHistory |  |
| is_delinquent | stripeCustomers |  |
| n_max_renewals | stripeInvoicesView |  |
| n_paid_intervals | stripeInvoicesView |  |
| n_plans_total | stripeInvoicesView |  |
| n_subscriptions_total | stripeInvoicesView |  |
| net_transaction_amount_in_past_365_days | stripeBalanceHistory |  |
| payment_method_details_card_network | stripeCharges |  |
| refund_count | stripeBalanceHistory |  |
| refund_count_in_past_365_days | stripeBalanceHistory |  |
| refund_in_past_365_days | stripeBalanceHistory |  |
| sales_in_past_365_days | stripeBalanceHistory |  |
| shipping_address_country | stripeCharges |  |
| shipping_address_state | stripeCharges |  |
| total_active_plan_amount | stripeInvoicesView |  |
| total_active_plans | stripeInvoicesView |  |
| total_active_subscriptions | stripeInvoicesView |  |
| total_amt_spent | stripeBalanceHistory |  |
| total_failed_charge_amount | stripeCharges |  |
| total_failed_charge_count | stripeCharges |  |
| total_fees | stripeBalanceHistory |  |
| total_net_transaction_amount | stripeBalanceHistory |  |
| total_refunds | stripeBalanceHistory |  |
| total_sales | stripeBalanceHistory |  |
| total_transactions | stripeBalanceHistory |  |
| transactions_in_past_365_days | stripeBalanceHistory |  |

