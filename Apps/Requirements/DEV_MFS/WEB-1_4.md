---
title: Book Actual Labour
description: Book Actual Labour
published: true
date: 2024-02-22T13:56:33.297Z
tags: 
editor: markdown
dateCreated: 2023-09-21T17:56:05.378Z
---

# Book Actual Labour

> **Requirement Specification**
> Date: 01/01/23
> Prepared By: Peter Roden
> Prepared for: Internal Development
{.is-info}

## Business Requirements

> **Why** are we making the change?
> To record the actual time (costs) taken for a service call and reflect those on the WIP activity, to provide accurate revenue results.
{.is-info}

<br/>

## Functional Requirements

> Note
> This is not configurable
{.is-danger}

## Labour Bookings
These need to reflect actual start stop times, if a job is paused, the labour is ended and restarted upon resuming.
> For example, minimum labour 30 mins, 15 min increments
> 31 mins taken, labour booking = 31 mins
{.is-info}


## Service Job Costs

The service call centre, line pricing details should show the following

Estimated Service as Standard Epicor Process
Actual Service as Standard Epicor Process
Billable service to be the rounded up amount based on minimum labour and labour increments

> - For example, minimum labour 30 mins, 15 min increments
> - 31 mins taken, billable = 45 mins
{.is-info}



## Technicial Requirements

There are three types of jobs

- Record Time
- Manual Entry
- Fixed Costs

These will display on field service and update Epicor in the following ways:
<br/>
| Time Type | Description |
| --- | --- | --- | --- |
| Actual time | The actual time worked, unrounded, according to the time the tasks were started and finished |
| Entered time | The time entered for manual entry jobs |
| Billable time | The billable time taking into account minimum labour time and roundings |
| Expected time | The time the task is expected to take according to the production standards|
| Actual Labour | Actual time multiplied by the labour rate on the task |
| Entered labour | Entered  time multiplied by the labour rate on the task |
| Billable Labour | Billable time multiplied by the labour rate on the task |
| Fixed Costs | The fixed costs of the job/call line |

<br/>
These times and costs are updated in the following ways:
<br/>

| Job Type | App Approval Screen | Epicor Labour Record | Epicor Call Actual | Epicor Call Billable |
| --- | --- | --- | --- | --- |
| Record Time | Billable time | Actual time | Actual labour | Billable labour |
| Manual Entry | Billable time | Entered time | Entered labour | Billable labour |
| Fixed Costs | No  time | Actual time | Actual Labour | Fixed Costs +  |

> 09-02-24 
Discussion to change on Fixed Costs
If there are fixed costs plus billable, these will be on top of fixed costs
{.is-info}


If there is more than one operation/task the Actual and Billable figures are the sum of all the tasks, apart from fixed costs which apply to the call line as a whole anyway

### API

#### App API

Add a field BillableJobHours to Complete Task message
Change the JobHours field to the actual time

<br/>

### Services

#### Epicor Sync

Update labour records and service call times according to rules above

<br/>

### Testing

All operations £24/hour
Minimum 30 mins
Fixed cost £50

| Test | Job | Labour Entry | Task | Billable | Time Recorded | App Time | App Cost | App Fixed Cost | Epicor Labour | Epicor Call Actual | Epicor Call Billable | Pass | 
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | 
| 1 | SRV0009500001 | Record Time | 10 | No | 4 mins | 4 mins | £0.00 | £0.00 | 4 mins | £1.60 | £0.00 | ✓ | 
| 2 | SRV0009580001 | Record Time | 10 | Yes | 5 mins | 5 mins | £12.00 | £0.00 | 5 mins | £2.00 | £12.00 | ✓ | 
| 3 | SRV0009560001 | Record Time | 10 | No | 4 mins | 4 mins | £0.00 | £0.00 | 4 mins | £2.80 | £0.00 | ✓ | 
|  |  |  | 20 | No | 3 mins | 3 mins |  |  | 3 mins |  |  |  | 
| 4 | SRV0009630001 | Record Time | 10 | No | 4 mins | 4 mins | £12.00 | £0.00 | 4 mins | £3.60 | £12.00 | ✓ | 
|  |  |  | 20 | Yes | 5 mins | 5 mins |  |  | 5 mins |  |  |  | 
| 5 | SRV0009640001 | Record Time | 10 | Yes | 4 mins | 4 mins | £24.00 | £0.00 | 4 mins | £3.20 | £24.00 | ✓ | 
|  |  |  | 20 | Yes | 4 mins | 4 mins |  |  | 4 mins |  |  |  | 
| 6 | SRV0009600001 | Manual Entry | 10 | No | 25 mins | 25 mins | £0.00 | £0.00 | 25 mins | £10 | £0.00 | ✓ | 
| 7 | SRV0009590001 | Manual Entry | 10 | Yes | 20 mins | 20 mins | £12.00 | £0.00 | 20 mins | £8 | £12.00 | ✓ | 
| 8 | SRV0009510001 | Manual Entry | 10 | No | 25 mins | 25 mins | £0.00 | £0.00 | 25 mins | £20 | £0.00 | ✓ | 
|  |  |  | 20 | No | 25 mins | 25 mins |  |  | 25 mins |  |  |  | 
| 9 | SRV0009570001 | Manual Entry | 10 | No | 25 mins | 25 mins | £12.00 | £0.00 | 25 mins | £20 | £12.00 | ✓ | 
|  |  |  | 20 | Yes | 25 mins | 25 mins |  |  | 25 mins |  |  |  | 
| 10 | SRV0009550001 | Manual Entry | 10 | Yes | 25 mins | 25 mins | £24.00 | £0.00 | 25 mins | £20 | £24.00 | ✓ | 
|  |  |  | 20 | Yes | 25 mins | 25 mins |  |  | 25 mins |  |  |  | 
| 11 | SRV0009540001 | Fixed Costs | 10 | No | 5 mins | 5 mins | £0.00 | £50.00 | 5 mins | £2 | £50.00 | ✓ | 
| 12 | SRV0009520001 | Fixed Costs | 10 | Yes | 4 mins | 4 mins | £12.00 | £50.00 | 4 mins | £1.60 | £68.00 | ✓ | 
| 13 | SRV0009530001 | Fixed Costs | 10 | No | 10 mins | 10 mins | £0.00 | £50.00 | 10 mins | £5.20 | £50.00 | ✓ | 
|  |  |  | 20 | No | 3 mins | 3 mins |  |  | 3 mins |  |  |  | 
| 14 | SRV0009610001 | Fixed Costs | 10 | No | 4 mins | 4 mins | £12.00 | £50.00 | 4 mins | £3.20 | £62.00 | ✓ | 
|  |  |  | 20 | Yes | 4 mins | 4 mins |  |  | 4 mins |  |  |  | 
| 15 | SRV0009620001 | Fixed Costs | 10 | Yes | 4 mins | 4 mins | £24.00 | £50.00 | 4 mins | £2.40 | £74.00 | ✓ | 
|  |  |  | 20 | Yes | 2 mins | 2 mins |  |  | 2 mins |  |  |  | 