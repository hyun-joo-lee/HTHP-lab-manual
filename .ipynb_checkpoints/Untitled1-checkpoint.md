---
jupyter:
  jupytext:
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.11.5
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# 1) Calculate Distance

```python
import math
```

```python
# Transform deg to rad
φ1 = lat1 * math.pi / 180; 
φ2 = lat2 * math.pi / 180; 
λ1 = lon1 * math.pi / 180; 
λ2 = lon2 * math.pi / 180; 

# Calculate Azimuth
y = math.sin(λ2 - λ1) * math.cos(φ2); 
x = math.cos(φ1) * math.sin(φ2) - math.sin(φ1) * math.cos(φ2) * math.cos(λ2 - λ1); 
θ = math.atan2(y, x)
if θ>0:
    θ = θ
elif θ<0:
    θ = θ+2*math.pi

# Calculate A B C
A = abs(λ1-λ2)
B = θ
C = 0
if B>math.pi:
    C = B - math.pi
else:
    C = B + math.pi

# Check rule 1 and calculate a b c
if A+B+C>math.pi:
    b = 90-lat2
    c = 90-lat1
    a = math.cos(math.radians(b))*math.cos(math.radians(c)) + math.sin(math.radians(b))*math.sin(math.radians(c))*math.cos(A)
    a = math.acos(a)
    # Transform rad to deg
    distance_deg = (a * 180 / math.pi)
    distance_km = 6378.1370 * a
else:
    print("Calculate again")
```

```python
# New York city(1) - Dakar(2)
lat1 = 40.73061; 
lon1 = -73.935242; 

lat2 = 14.716677; 
lon2 = -17.467686;
```

```python
print("New York city to Dakar")
print("distance in degree:", distance_deg)
print("distance in km:", distance_km, "km")
```

```python
# Dakar(1) - San Juan(2)
lat1 = 14.716677; 
lon1 = -17.467686;

lat2 = 18.466333; 
lon2 = -66.105721; 
```

```python
print("Dakar to San Juan")
print("distance in degree:", distance_deg)
print("distance in km:", distance_km, "km")
```

```python
# San Juan(1) - New York city(2)
lat1 = 18.466333; 
lon1 = -66.105721; 

lat2 = 40.73061; 
lon2 = -73.935242; 
```

```python
print("San Juan to New York city")
print("distance in degree:", distance_deg)
print("distance in km:", distance_km, "km")
```

# 2) Calculate Azimuth


pt 1 = New York city  
pt 2 = Dakar, Senegal  
pt 3 = San Juan, Puerto Rico

```python
print ("Azimuth from pt 1 to pt 2:", a)
```

```python
print ("Azimuth from pt 2 to pt 3:", a)
```

```python
print ("Azimuth from pt 3 to pt 1:", a)
```

# 3) Calculate spreading rate
This is half-spreading rate, which shows growing rate of one plate.

```python
#1300km/70Ma
print("Average spreading rate for 70Ma is", 130000000/70000000, "cm/year")
```
