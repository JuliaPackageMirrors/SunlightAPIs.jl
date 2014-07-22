# Sunlight.jl

##### A Julia package for interfacing with the Sunlight Foundation's APIs

## Quick start

```julia
```


## Influence Explorer API

### Common Parameters
Many of methods in the Influence Explorer API accept similar arguments. To reduce redundancy, these are documented once, below. Not all methods accept all common parameters - be sure to check the function signature in the docs further down.

- `auth`: Your Sunlight API key ([get one here](http://sunlightfoundation.com/api/)).
- `entity_id`: The transparencydata ID of the entity that you'd like to look up.
- `cycle`: Use to limit results by cycle(s).
- `limit`: Use to limit the number of results to be returned.

### Entity Lookup Methods

#### Entity Search
Search for politicians, individuals, organizations or industries with a given name.

```julia
entity_search(auth::String, search_str; entity_type = nothing)

entity_search(search_str; auth = "", entity_type = nothing)
```
- `search`: The name to search for. Spaces should be URL encoded or represented as a plus sign (+). There are no logical operators and no grouping.
- `type`:   Filter results to a particular type of entity.
    * `"politician"`
    * `"organization"`
    * `"individual"`
    * `"industry"`


#### Entity Info
Get general information about the given entity.

```julia
entity_info(auth::String, entity_id; cycle = nothing)

entity_info(entity_id; auth = "", cycle = nothing)
```


### Politician Aggregates Methods

#### Top Politicians
By contributions received, in dollars.

```julia
top_politicians(auth::String; limit = 16, cycle = nothing)

top_politicians(; auth = "", limit = 16, cycle = nothing)
```


#### Top Contributors
The top contributing organizations to a given candidate. Giving is broken down into money given directly (by the organization's PAC), versus money given by individuals employed by or associated with the organization.

```julia
top_contributors(auth::String, entity_id; limit = nothing, cycle = nothing)

top_contributors(entity_id; auth = "", limit = nothing, cycle = nothing)
```


#### Top Industries
Top contributing industries, ranked by dollars given.

```julia
top_industries(auth::String, entity_id; limit = nothing, cycle = nothing)

top_industries(entity_id; auth = "", limit = nothing, cycle = nothing)
```


#### Unknown Industries
Contribution count and total for a politician from unknown industries.

```julia
unknown_industries(auth::String, entity_id; cycle = nothing)

unknown_industries(entity_id; auth = "", cycle = nothing)
```


#### Top Sectors
Contribution totals by sector to a given politician. Sectors are codified by letter:
- `A`: Agribusiness
- `B`: Communications/Electronics
- `C`: Construction
- `D`: Defense
- `E`: Energy/Natural Resources
- `F`: Finance/Insurance/Real Estate
- `H`: Health
- `K`: Lawyers and Lobbyists
- `M`: Transportation
- `N`: Misc. Business
- `Q`: Ideology/Single Issue
- `P`: Labor
- `W`: Other
- `Y`: Unknown
- `Z`: Administrative Use

```julia
top_sectors(auth::String, entity_id; limit = nothing, cycle = nothing)

top_sectors(entity_id; auth = "", limit = nothing, cycle = nothing)
```


#### Local Breakdown
A breakdown of how much of the money raised by a politician came from inside or outside their home state.

```julia
local_breakdown(auth::String, entity_id; cycle = nothing)

local_breakdown(entity_id; auth = "", cycle = nothing)
```


#### Contributor Type Breakdown
A breakdown of how much of the money raised came from individuals versus organzations (PACs).

```julia
contributor_breakdown(auth::String, entity_id; cycle = nothing)

contributor_breakdown(entity_id; auth = "", cycle = nothing)
```


#### FEC Summary
Latest figures from the FEC's summary report.

```julia
fec_summary(auth::String, entity_id)

fec_summary(entity_id; auth = "")
```


#### FEC Independent Expenditures
Top independent expenditures for and against a politician.

```julia
fec_independent_expenditures(auth::String, entity_id)

fec_independent_expenditures(entity_id; auth = "")
```


### Individual Aggregates

#### Top Individuals
By contributions given, in dollars.

```julia
top_individuals(auth::String; limit = 16, cycle = nothing)

top_individuals(; auth = "", limit = 16, cycle = nothing)
```


#### Top Recipient Organizations
Top organizations to which this individual has donated, by dollars given.

```julia
top_recipient_organizations(auth::String, entity_id; limit = nothing, cycle = nothing)

top_recipient_organizations(entity_id; auth = "", limit = nothing, cycle = nothing)
```


#### Top Recipient Politicians
Politicians to whom the individual has given the most money.

```julia
top_recipient_politicians(auth::String, entity_id; limit = nothing, cycle = nothing)

top_recipient_politicians(entity_id; auth = "", limit = nothing, cycle = nothing)
```


#### Party Breakdown
Details on how much an individual gave to each party.

```julia
party_breakdown(auth::String, entity_id; cycle = nothing)

party_breakdown(entity_id; auth = "", cycle = nothing)
```


#### Lobbying Registrants
A list of the lobbying firms which employed an individual.

```julia
lobbying_registrants(auth::String, entity_id; limit = nothing, cycle = nothing)

lobbying_registrants(entity_id; auth = "", limit = nothing, cycle = nothing)
```


#### Lobbying Clients
Clients an individual (lobbyist) was contracted to work for.

```julia
lobbying_clients(auth::String, entity_id; limit = nothing, cycle = nothing)

lobbying_clients(entity_id; auth = "", limit = nothing, cycle = nothing)
```


#### Lobbying Issues
Issue areas a lobbyist worked on.

```julia
lobbying_issues(auth::String, entity_id; limit = nothing, cycle = nothing)

lobbying_issues(entity_id; auth = "", limit = nothing, cycle = nothing)
```
