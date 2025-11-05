 
##  Tabby Payment Integration Guide for Front-End Teams

This guide outlines the steps required to successfully integrate Tabby as a payment option on the product details or checkout page.

---

## 1. Implement Tabby Snippet

The Tabby Snippet is crucial for informing customers about the "Pay in X" option and its benefits, usually displayed on the **Product Details Page** or, if unavailable, on the **Payment Checkout Page**.

| Aspect | Details |
| :--- | :--- |
| **Placement** | On the **Product Details Page** near the price, or on the **Payment Checkout Page**. |
| **Description** | Implement the Snippet as described in the Tabby documentation, including the required branding (logo, title, description). |
| **Interaction** | If the Snippet is tapped/clicked, it must open the specific informational link provided by Tabby, with all required query parameters (e.g., product price, currency). |

* **Snippet Interaction Link (Example):** `https://checkout.tabby.ai/promos/product-page/installments/{lang}/?price={PRICE}&currency={CURRENCY}&merchant_code={MERCHANT_CODE}&public_key={PUBLIC_KEY}`

* `lang`  according to current lang set to ar or en
* `price` (e.g., `100` final total price)
* `currency` (e.g., `SAR`)
* `merchant_code` (e.g., `SBA`)
* `public_key` (e.g., `pk_xyz`)

* [Link to Tabby's Snippet Implementation Guide](https://docs.tabby.ai/pay-in-4-custom-integration/on-site-messaging)
 
---

## 2. Present Tabby as a Payment Option

Once the customer is ready to select a payment method, Tabby must be clearly displayed and selectable.

| Aspect | Details |
| :--- | :--- |
| **Placement** | Within the list of **Payment Options** on the Checkout page. |
| **Branding** | Use the required Tabby **logo** and **title** (e.g., "Tabby - Pay in 4"). |
| **Description** | Include the required **description** (e.g., "Split your purchase into 4 interest-free payments") as specified in the docs. |

>❗ The Tabby session must be initiated and handled in the same tab on the website. No new tab or window should be opened when redirecting to Tabby's payment flow.

### 🔗 Required Documentation Links

* [Link to Tabby's Branding and Payment Option Display Guidelines](https://docs.tabby.ai/pay-in-4-custom-integration/checkout-flow#tabby-on-checkout)
* [Link to Tabby's Logo](https://cdn.tabby.ai/assets/logoimg.png)

---

## 3. Background Pre-scoring Check

The front-end must handle scenarios where Tabby's payment option is unavailable due to limits or rejection, ensuring a clear user experience.

| Scenario | Test Case | Front-End Action |
| :--- | :--- | :--- |
| **Price Too High** | Attempt to checkout with a product price significantly **above the limit** (e.g., 1,000,000 SAR/AED). | Tabby must be **unselectable** and display the rejection reason. |
| **Price Too Low** | Attempt to checkout with a product price significantly **under the limit** (e.g., 10 SAR/AED). | Tabby must be **unselectable** and display the rejection reason. |
| **Rejected Credentials** | Use test credentials known to be rejected (provided in the gateway docs). | Tabby must be **unselectable** and display the rejection reason. |
| **Rejection Message** | Ensure the rejection message is **identical** to the documentation in both **English** and **Arabic**. | Work with the backend team to confirm the exact strings. |

### 🔗 Required Documentation Links

 * [Link to Tabby's Background Pre-scoring Check](https://docs.tabby.ai/pay-in-4-custom-integration/checkout-flow#background-pre-scoring-check)*

---

## 4. Collaboration with the Backend Team

Close collaboration is essential for smooth integration and comprehensive testing.

* [Full Testing Checklist](https://docs.tabby.ai/pay-in-4-custom-integration/full-testing-checklist)

* [Testing Credentials](https://docs.tabby.ai/testing-guidelines/testing-credentials)

---

 
## 5. Provide Testing Credentials For Tabby QA Team 

 After verifying that everything works correctly and all items in the test checklist are covered, each platform should provide one account with at least 5 paid orders using any available payment option.

Additionally, please register an account with the rejected credentials to assist the Tabby QA team in their testing process.
