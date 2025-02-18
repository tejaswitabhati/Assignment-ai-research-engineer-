import random
from datetime import datetime, timedelta


STORES = ["Amazon", "Zara", "H&M", "ASOS", "Nike"]


MOCK_PRODUCTS = {

    "Nike Shoes": {"Amazon": 120, "Zara": 130, "H&M": 125, "ASOS": 119, "Nike": 140},
    
    "Denim Jacket": {"Amazon": 60, "Zara": 65, "H&M": 55, "ASOS": 58, "Nike": None},
    
    "Leather Bag": {"Amazon": 150, "Zara": 140, "H&M": 155, "ASOS": 148, "Nike": None},
    
    "Floral Skirt": {"Amazon": 35, "Zara": 38, "H&M": 30, "ASOS": 32, "Nike": None},
    
    "White Sneakers": {"Amazon": 65, "Zara": 68, "H&M": 60, "ASOS": 70, "Nike": None}}


RETURN_POLICIES = {

    "Amazon": "30-day return with free shipping.",
    
    "Zara": "Return within 14 days, customer pays return fee.",
    
    "H&M": "Return within 30 days, refund in original payment method.",
    
    "ASOS": "45-day return policy, free return shipping.",
    
    "Nike": "60-day trial period for most items.",
    
    "SiteB": "Returns accepted within 21 days with a full refund."}


PROMO_CODES = {
  
    "SALE10": 0.10,  
    
    "FASHION20": 0.20,  
    
    "WELCOME5": 0.05, 
    
    "SAVE10": 0.10  
    
}


# #E-Commerce Search Aggregator 

def search_products(query, price_limit=None, size=None):

    results = []
    
    for product in MOCK_PRODUCTS:
    
        if query.lower() in product.lower():
        
            stores_with_product = {store: price for store, price in MOCK_PRODUCTS[product].items() if price}
            
            filtered_stores = {store: price for store, price in stores_with_product.items() if price_limit is None or price <= price_limit}
            
            if filtered_stores:
            
                results.append({"product": product, "stores": filtered_stores, "size": size})
                
    return results if results else "No matching products found."
    

# #Shipping Time Estimator

def estimate_shipping(location, delivery_date):

    base_cost = random.randint(5, 15)  
    
    estimated_days = random.randint(2, 7)
    
    estimated_delivery = datetime.now() + timedelta(days=estimated_days)
    
    return {
    
        "Location": location,
        
        "Requested Delivery": delivery_date,
        
        "Estimated Cost": f"${base_cost}",
        
        "Expected Delivery": estimated_delivery.strftime("%Y-%m-%d")
        
    }
    

#  #Discount / Promo Checker

def apply_discount(base_price, promo_code):

    discount = PROMO_CODES.get(promo_code, 0)
    
    final_price = base_price * (1 - discount)
    
    return {
    
        "Base Price": f"${base_price}",
        
        "Discount Applied": f"{int(discount * 100)}%" if discount > 0 else "Invalid code",
        
        "Final Price": f"${final_price:.2f}"
        
    }
    

# #Price Comparison

def compare_prices(product_name):

    return MOCK_PRODUCTS.get(product_name, "Product not found in competitor stores.")
    

# #Return Policy 

def check_return_policy(store_name):

    return RETURN_POLICIES.get(store_name, "Store not found.")
