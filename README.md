# MerchantItems

Split a single MQ XML input message into multiple XML output files — one per merchant.

## Project Overview

This project demonstrates how to:

- Read an XML message from an MQ input
- Parse and group data by merchant
- Build separate XML files dynamically
- Set output file names based on merchant values

The goal is to take a flat list of `<Item>` elements and generate one output XML file per merchant containing that merchant’s items.

## Input Format

The input message is a single XML:

```xml 
<Items>
    <Item>
        <Merchant>C21</Merchant>
        <ItemType>Item1</ItemType>
        <ItemPrice>120</ItemPrice>
    </Item>
    <Item>
        <Merchant>B24</Merchant>
        <ItemType>item2</ItemType>
        <ItemPrice>23</ItemPrice>
    </Item>
    <Item>
        <Merchant>A22</Merchant>
        <ItemType>item3</ItemType>
        <ItemPrice>332</ItemPrice>
    </Item>
    …
</Items>
```

## Output Format

For each merchant, the solution generates a file named <MerchantCode>.xml, with content like:

```xml
<Merchant name="C21">
    <ItemsList>
        <Item type="Item1" price="120"/>
        <Item type="item5" price="213"/>
        <Item type="item9" price="540"/>
    </ItemsList>
</Merchant>
```

## Key ESQL Concepts Used

- XML parsing and navigation

- Looping over repeated fields

- Building output messages dynamically

- Setting output file names at runtime


## Getting Started

1. Import the message flow into IBM App Connect / ACE.

2. Configure the input node to read from MQ.

3. Configure output nodes (or a dynamic file output).

4. Deploy and test with the provided sample input.

Example Output Files

- C21.xml — contains only the items for merchant C21

- A22.xml — contains only the items for merchant A22

- B24.xml — contains only the items for merchant B24
