**TASK 1**

query_a = "Find a floral skirt under $40 in size S. Is it in stock, and can I apply a discount code ‘SAVE10’?"

task_a_result = search_products("Floral Skirt", price_limit=40, size="S")


if isinstance(task_a_result, list) and task_a_result:

    promo_result = apply_discount(task_a_result[0]["stores"][list(task_a_result[0]["stores"].keys())[0]], "SAVE10")
    
else:

    promo_result = "No matching products found to apply discount."
    

print(query_a)

print("Search Result:", task_a_result)

print("Promo Applied:", promo_result)



**TASK 2**

query_b = "I need white sneakers (size 8) for under $70 that can arrive by Friday."

task_b_result = search_products("White Sneakers", price_limit=70, size=8)

shipping_result = estimate_shipping("New York", "Friday")


print(query_b)

print("Search Result:", task_b_result)

print("Shipping Estimate:", shipping_result)





**TASK 3**

query_c = "I found a ‘casual denim jacket’ at $80 on SiteA. Any better deals?"

task_c_result = compare_prices("Denim Jacket")


print(query_c)

print("Competitor Prices:", task_c_result)




**TASK 4**

query_d = "I want to buy a cocktail dress from SiteB, but only if returns are hassle-free. Do they accept returns?"

task_d_result = check_return_policy("SiteB")


print(query_d)

print("Return Policy:", task_d_result)




**TASK 5**

query_e = "Find Nike Shoes under $130, estimate shipping to Los Angeles, apply promo code SALE10, and compare prices."

task_e_search = search_products("Nike Shoes", price_limit=130)

task_e_shipping = estimate_shipping("Los Angeles", "2024-02-28")

task_e_discount = apply_discount(120, "SALE10")

task_e_comparison = compare_prices("Nike Shoes")


print(query_e)

print("Search:", task_e_search)

print("Shipping:", task_e_shipping)

print("Discount Applied:", task_e_discount)

print("Price Comparison:", task_e_comparison)

