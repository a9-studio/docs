---
title: Billing threshold in {{ billing-name }}
description: A billing threshold is a negative personal account balance. The billing threshold is how post-payment is implemented in {{ yandex-cloud }}.
---

# Billing threshold

A billing threshold is a negative [personal account balance](../concepts/personal-account.md#balance). The billing threshold is how post-payment is implemented in {{ yandex-cloud }}. In other words, this is the limit after which {{ yandex-cloud }} can:
* Require that you settle your arrears before the reporting period.
* Suspend your use of resources.

Your billing threshold is valid for 1 month.

{% note alert %}

The billing threshold amount and the total arrears when you are blocked may be different, since access to resources is not suspended immediately. The fact that you have a billing threshold does not guarantee that you will not spend over your threshold.

{% endnote %}

The billing threshold is only valid when you select a bank card as your payment method. If you do, when you reach your threshold, an attempt will be made to debit your card to cover what you owe.

## Billing threshold amount {#amount}

The billing threshold amount is calculated individually and depends on a combination of factors, including:
- [Billing account type](../concepts/billing-account.md#ba-types).
- Amount for resources consumed.
- Your financial standing.

You can view the information on the billing threshold amount in [{{ billing-name }}]({{ link-console-billing }}), in the top-right section of the **{{ ui-key.yacloud_billing.billing.account.switch_overview }}** page, along with the current balance details.

## Enabling a billing threshold {#enable}

The billing threshold is enabled automatically after the [paid version is activated](../operations/activate-commercial.md) and the first reporting period ends.

{% note info %}

The billing threshold cannot be disabled and is valid until [the billing account is deleted](../operations/delete-account.md). To change the billing threshold, create a [new support ticket]({{ link-console-support }}).

{% endnote %}

## Using a billing threshold {#using}

The billing threshold can only be used if you don't have a [grant](../concepts/bonus-account.md) and [your personal account balance](../concepts/personal-account.md#balance) is zero. If you use the billing threshold, you go into arrears as your personal account balance falls below zero.

If you are using a bank account to pay for {{ yandex-cloud }} resources, a billing threshold will not apply.

## Amount due {#sum}

{% list tabs group=customers %}

- Individuals {#individuals}

  You can track the [balance of your personal account](../concepts/personal-account.md#balance) in [{{ billing-name }}]({{ link-console-billing }}) on the **{{ ui-key.yacloud_billing.billing.account.switch_overview }}** page:
  * Your balance automatically reduces as you consume resources.
  * You can view your usage history on the [usage details](../operations/check-charges.md) page.
  * When you [credit funds](../payment/payment-methods-individual.md), your balance increases. The top-up record is logged to the [payment history](../operations/check-bill-history.md).

  For more information, see [Topping up your personal account](../operations/pay-the-bill.md#individuals).

- Businesses and individual entrepreneurs {#businesses}

  You can find the amount due in the [reporting documents](../payment/documents.md) that {{ yandex-cloud }} sends to customers each month.

{% endlist %}

## Paying arrears {#arrears}

The outstanding charges shall be paid within the deadline stipulated in the [agreement](../concepts/contract.md). The [payment method](../payment/index.md) depends on your legal status. You cannot use [grants](bonus-account.md) to pay off arrears.

{% note info %}

We recommend that you keep track of the money you spend from your personal account and [maintain a positive balance at all times](../operations/pay-the-bill.md). If your personal account balance exceeds the billing threshold or you fail to pay the arrears within the timeline set forth in the agreement, {{ yandex-cloud }} reserves the right to change the status of your billing account to [SUSPENDED](../concepts/billing-account-statuses.md).

{% endnote %}

For more information, see the following sections:
* For individuals
    * [Bank card payments](../payment/payment-methods-individual.md)
    * [Billing cycle](../payment/billing-cycle-individual.md)

* Businesses and individual entrepreneurs:
    * [Bank account transfer](../payment/payment-methods-business.md)
    * [Bank card payments](../payment/payment-methods-card-business.md)
    * [Billing cycle](../payment/billing-cycle-business.md)
