---
title: "PostgreSQL Basics with Art"
author: "Osman Cakir"
date: 2019-03-09
description: "PostgreSQL Basics."
type: technical_note
draft: false
---

## Create Table

Let's create a table called painters and save the data about the most expensive paintings in the world.

{{< highlight sql >}}
-- Create table called painters
CREATE TABLE painters (
    -- string variable
    painter varchar(255),
    -- string variable
    painting varchar(255),
    -- integer variable
    sold (million Euros) int
)
{{< /highlight >}}

## Insert Rows

{{< highlight sql >}}
-- Insert into the table painters
INSERT INTO adventurers (painter, painting, sold (million Euros))
VALUES ('Leonardo da Vinci', 'Salvator Mundi', 382),
       ('Willem de Kooning', 'Interchange', 254),
       ('Paul Cézanne', 'The Card Players', 212 ),
       ('Paul Gauguin', 'Nafea Faa Ipoipo', 172),
       ('Jackson Pollock', 'Number 7A', 169.8),
       ('Mark Rothko', 'No. 6 (Violet, Green and Red)', 157,9)
{{< /highlight >}}

## Retrieve Rows

{{< highlight sql >}}
-- Retrieve all rows from table
SELECT * FROM adventurers
{{< /highlight >}}
<table border="1" style="border-collapse:collapse">
<tr><th>painter</th><th>painting</th><th>sold (million Euros)</th></tr>
<tr><td>Leonardo da Vinci</td><td>Salvator Mundi</td><td>382</td></tr>
<tr><td>Willem de Kooning</td><td>Interchange</td><td>254</td></tr>
<tr><td>Paul Cézanne</td><td>The Card Players</td><td>212</td></tr>
<tr><td>Paul Gauguin</td><td>Nafea Faa Ipoipo</td><td>172</td></tr>
<tr><td>Jackson Pollock</td><td>Number 7A</td><td>169.8</td><</tr>
<tr><td>Mark Rothko</td><td>No. 6 (Violet, Green and Red)</td><td>157.9</td></tr></table>

to be continued...