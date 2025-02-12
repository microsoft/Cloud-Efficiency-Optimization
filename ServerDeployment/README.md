# Efficient Cloud Server Deployment Under Demand Uncertainty - Data



## Data Description

This dataset accompanies the paper “Efficient Cloud Server Deployment Under Demand Uncertainty”. Each .pkl file contains an instance for the two-stage problem, which consists of the following:

1.	`demand_costs` (dict): key is a tuple (demand, datacenter, date) and value is the cost for docking the demand in that datacenter on that date (this value corresponds to the coefficient of $z_{d,\ell,t}$ in the objective, i.e., $c_{d,t}-u_d$)
2.	`shipping_costs` (dict): key is a tuple (demand, supply) and value is the shipping cost if the demand is deployed using that supply
3.	`row_costs` (dict): key is a datacenter and value is the cost of building a new row in that datacenter
4.	`sum_undock` (float): this corresponds to the constant term in the first-stage objective $\sum_d u_d$
5.	`demands` (list): each item is a demand ID
6.	`supplies` (dict): key is the supplier ID and value is the available inventory of that supplier 
7.	`existing_rows` (dict): key is a datacenter and value is the existing number of rows in that datacenter
8.	`datacenters` (list): each item of the list is a datacenter
9.  `datacenter_capacities` (dict): key is a datacenter and value is the capacity of the datacenter for empty existing rows and new rows ($\zeta_{\ell}$)
9.	`throughput_capacity` (list of tuples): each tuple corresponds to a throughput constraint; the first item of the tuple is a list of datacenters on which the throughput constraint applies and the second item a list of (date, capacity) tuples denoting the available throughput capacity on each date
10.	`capacity_indices` (list): each item is an index for `throughput_capacity`
11.	`center_throughput` (dict): key is a datacenter and value is a list of indices of the throughput capacity constraints in which the datacenter participates
12.	`dates` (list): each item is a date for deployment
13.	`potential_center_dates` (list): each item is a tuple (datacenter, date) and denotes that that date is valid for docking in that datacenter
14.	`completion_date` (date): the start of period $T_2$
15.	`completion_date_index` (int): index of `completion_date` in the dates list
16.	`sample_size` (int): number of scenarios
17.	`sample_demand_costs` (list of dicts): key is a tuple (demand, datacenter, date) and value is the cost for docking the demand in that datacenter on that date (this value corresponds to the coefficient of $z_{d,\ell,t}$ in the objective, i.e., $c_{d,t}-u_d$); there is one dict in the list per scenario and its meaning is similar to the `demand_costs` but for the stochastic demands of that scenario
18.	`sample_shipping_costs` (list): each item corresponds to one scenario and is a dict where the key is a tuple (demand, supply) and the value is the shipping cost if that demand is deployed using that supply
19.	`sum_sample_undock` (float): the sum of $u_d$ for all demands in all scenarios 
20.	`sample_undock_costs_sum` (list): each item corresponds to one scenario and is the sum of $u_d$ for all demands in that scenario
21.	`sample_demands` (list): each item corresponds to one scenario and is a list of demand IDs that belong to that scenario
22.	`sample_potential_center_dates`  (list): each item corresponds to one scenario and is a set of tuples (datacenter, date) denoting that that date is valid for docking in that datacenter


## How to Read

```python
import pickle
with open(data_path + 'data.pkl', 'rb') as out:
    data = pickle.load(out)

(
    demand_costs,
    shipping_costs,
    row_costs, 
    sum_undock,
    demands,
    supplies, 
    existing_rows,
    datacenters,
    datacenter_capacities,
    throughput_capacity,
    capacity_indices,
    center_throughput,
    dates, 
    potential_center_dates,
    completion_date,
    completion_date_index,
    sample_size,
    sample_demand_costs,
    sample_shipping_costs,
    sum_sample_undock,
    sample_undock_costs_sum,
    sample_demands,
    sample_potential_center_dates,
) = data  

```