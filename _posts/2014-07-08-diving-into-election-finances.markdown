---
layout: post
title: "Diving into election finances"
date: 2014-07-08 19:17
comments: true
categories: election
---
After talking to the electoral commission yesterday, I got interested in what local candidates normally spend on their campaigns.

Fortunately, this is all open data. The Electoral Commission publish the statistics about election spending on their website, all under the Open Government License. All figures in this article come from them.

There is one particular dataset which we'll dive into here; the [candidate spending in the 2010 general election](http://www.electoralcommission.org.uk/find-information-by-subject/elections-and-referendums/past-elections-and-referendums/uk-general-elections/candidate-election-spending). This lists all candidates in the general election of 2010, what they spent, what they raised, and even better, what the split of spending was. It also includes the number of votes they gained, so you could do some handy analysis of spending vs seats gained, perhaps. There's lots of data in there, so what follows are excerpts, not the whole lot.

## Total spending

Let's look at campaign spending first.

We had 8 candidates in the last election. During the long campaign (see yesterday's post), they were allowed to spend **£30,429.48**. During the short campaign, they were allowed to spend **£12,579.48**.

<table class="table table-striped">
<thead>
<tr>
<th></th>
<th> Party </th>
<th> Votes </th>
<th> Long Campaign Spend </th>
<th> Short Campaign Spend</th>
</tr>
</thead>
<tbody>
<tr>
<td></td>
<td> Conservatives </td>
<td>   29,447 </td>
<td> £3,577.41 </td>
<td> £7,564.69</td>
</tr>
<tr>
<td></td>
<td> Lib Dems </td>
<td> 17,987 </td>
<td> £1,158.83 </td>
<td> £4,446.94</td>
</tr>
<tr>
<td></td>
<td> Labour Party </td>
<td> 4,189 </td>
<td> £75.75 </td>
<td> £1,460.67</td>
</tr>
<tr>
<td></td>
<td> UKIP </td>
<td> 2,839 </td>
<td> £350.00 </td>
<td> £2,299.20</td>
</tr>
<tr>
<td></td>
<td> Green Party </td>
<td> 570 </td>
<td> £0.00 </td>
<td> £0.00</td>
</tr>
<tr>
<td></td>
<td> Christian Party </td>
<td> 469 </td>
<td> £0.00 </td>
<td> £1,056.50</td>
</tr>
<tr>
<td></td>
<td> Peace Party </td>
<td> 253 </td>
<td> £0.00 </td>
<td> £400.00</td>
</tr>
<tr>
<td></td>
<td> Independent </td>
<td> 87 </td>
<td> £0.00 </td>
<td> £501.09</td>
</tr>
</tbody>
</table>

[![2010 Horsham Campaign Spending](/images/2010_horsham_campaign_spending.png)](https://plot.ly/~Floppy/1)

So, what can we learn from this?

1. The total cost of the campaign was not much over £11k for the highest-spending party. That's reassuring.

2. None of them spent anywhere near the maximum allowed.

3. Most of the spending happens in the short campaign; this makes sense, as that's when your mailouts happen, etc.

4. The Green Party spent *nothing*. That explains why I never got a leaflet telling me about the candidate. I'm going to ignore anyone else who suggests I'll split their vote now, as they quite obviously *aren't interested* here.

## Where does the money go?

Let's dig into a bit more detail on what that money is spent on. We'll just look at the Conservatives here, as they have the largest spend.

<table class='table table-striped'>
<thead>
<tr>
<th></th>
<th> Category </th>
<th> Spend </th>
</tr>
</thead>
<tbody>
<tr>
<td></td>
<td> Advertising </td>
<td> £966.32 </td>
</tr>
<tr>
<td></td>
<td> Leaflets </td>
<td> £4,897.67 </td>
</tr>
<tr>
<td></td>
<td> Staff </td>
<td> £4,177.63 </td>
</tr>
<tr>
<td></td>
<td> Accommodation </td>
<td> £1,100.48 </td>
</tr>
</tbody>
</table>

This is really interesting for my planning. The actual cost of getting a leaflet to (presumably) every home in the constituency (which has 77,000 voters) is *under £5k*. That's a *lot* less than I expected, and should totally be crowdfundable. That's verified by the other parties as well - the Lib Dems spent a similar amount.

## Learning more

This has given me some really useful insights. I'd recommend having a dig into the figures for your area as well, you might find something interesting! I think this could be a good data-driven website as well - exposing this stuff through a nice data visualisation would be lovely; maybe a project for [Democracy Club](http://twitter.com/democlub)?

You can dig into the data at the link above, and [this guide](http://www.electoralcommission.org.uk/__data/assets/pdf_file/0011/163793/EPE-Part-3-Spending-and-donations-for-individual-candidates.pdf) from the Electoral Commission gives lots more detail on what it all means. It's for the 2014 EU elections, but the concepts are the same, so it's a decent reference. I'll be digging more into that guide as I go along, sorting out my own finances, so more of this to come.

Until next time...
