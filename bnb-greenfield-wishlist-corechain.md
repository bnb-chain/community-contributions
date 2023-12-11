# BNB Greenfield Core Chain Wishlist 

Welcome to the BNB Greenfield Challenge Wishlist! Our community has outlined exciting challenges to foster innovation and enhance the BNB Greenfield ecosystem. 



| Challenge                                                    | Importance | Status |
| ------------------------------------------------------------ | ---------- | ------ |
| [Leveraging BNB Greenfield for L1 Data Storage](#challenge-leveraging-bnb-greenfield-for-l1-data-storage) | High       | Active |
| [Empowering Greenfield with Advanced Analytics Support](#challenge-empowering-greenfield-with-advanced-analytics-support) | High       | Active |
| [Light-weight storage provider](#challenge-light-weight-storage-provider) | Medium     | Active |
| [Greenfield Tagging and Indexing Service](#challenge-greenfield-tagging-and-indexing-service) | High       | Active |
| [High-Performance Multipart Storage Solution on Greenfield](#challenge-developing-a-high-performance-multipart-storage-solution-on-greenfield) | High       | Active |

# Challenges

## Challenge: Leveraging BNB Greenfield for L1 Data Storage

### Main Objectives/Goals
1. Optimize L1 data storage using BNB Greenfield.
2. Reduce latency and enhance data accessibility.
3. Enable efficient retrieval of dormant or dead data.

### Challenge Description
The challenge seeks innovative solutions to optimize L1 data storage using
BNB Greenfield's decentralized capabilities. L1 chains often carry vast
amounts of historical data, including dormant or inactive content, leading
to increased latency.

The challenge aims to reduce this latency and enhance data accessibility
by migrating historical data to BNB Greenfield. This solution will enable
faster and smoother data retrieval on the EVM-compatible chain, resulting
in an improved user experience.

Additionally, the proposed solution should allow for efficient retrieval
of dormant or dead data whenever required, ensuring valuable information
remains accessible and not lost over time.

## Challenge: Empowering Greenfield with Advanced Analytics Support

### Main Objectives/Goals:

1. Revolutionize storage network analytics.
2. Create an intuitive analytics dashboard for greenfield data insights.
3. Build open-source block explorer and real-time status dashboards.

### Challenge Description:

The challenge seeks to revolutionize Greenfield by providing comprehensive
analytics support, enabling users to gain valuable data insights and
enhance the efficiency and effectiveness of their storage network activities. The
primary goal is to develop a powerful analytics ecosystem that encompasses
various essential elements.

The first objective is to design and implement an analytics dashboard that
offers users access to useful data insights. This dashboard will serve as
a centralized hub for users to explore and visualize different aspects,
such as gas costs, security metrics, and potential savings over a longer
timeframe. The focus is on creating an intuitive and user-friendly
interface that empowers users to make informed decisions based on
real-time data.

The second aspect of the challenge involves building an open-source block
explorer. This explorer should offer users the
ability to delve deep into the data, providing them with a comprehensive view of their Greenfield object management transactions and activities. This feature will promote
transparency and encourage in-depth research and analysis, leading to novel insights and discoveries.

Moreover, the challenge aims to develop status dashboards that
continuously monitor the health of the Greenfield network. These dashboards
will provide real-time updates on network performance, identifying
potential issues and areas for improvement. By offering network health
monitoring tools, users can proactively address challenges and ensure the
smooth operation of their storage network activities.


## Challenge: Light-weight storage provider

### Main Objectives/Goals:

1. Easy to setup and maintain storage provider
2. Decentralization of storage provider implementation

### Challenge Description:

Greenfield aims to allow users and storage provider maintainers to use a light-weighted storage provider that offers a new implementation of storage provider for easy management and setup. By using the light-weight storage provider, Greenfield allows users to create, configure, and manage storage resources with minimal overhead and complexity.

Considerations:

1. Greenfield is designed to be scalable, reliable, and secure, while also providing high performance and low latency.
2. Greenfield is ideal for applications that need fast and flexible storage solutions, such as web hosting, data analytics, media streaming, and more.

## Challenge: Greenfield Tagging and Indexing Service

### Main Objectives/Goals
1. Efficient Indexing and Database Integration

The system must efficiently store this tag data in a database to facilitate easy querying.

Emphasize the need for a scalable and optimized database schema that caters to tag-based searches.

2. Real-Time Synchronization with the Blockchain

The solution should detail the approach to maintaining data integrity and consistency during the synchronization process.

3. Advanced Query Interface for Tag Data

The interface should enable users to retrieve comprehensive information based on tag queries.

Highlight the need for various query capabilities, including:

- Retrieval of object or bucket IDs based on specific tags.
- Fetching all associated tags for a given object or bucket.
- Additional Considerations:

- Security and Privacy: Outline requirements for ensuring data security and user privacy in handling blockchain data and query processes.
- Documentation and User Guides: Proposals must include comprehensive documentation and user guides detailing system architecture, API usage, and examples.
- Testing and Validation: Emphasize the need for thorough testing methodologies, including unit tests, integration tests, and performance benchmarks.

### Challenge Description

Efficient data organization and management are critical components for decentralized storage. This challenge is proposed to incorporate a robust indexing system, drawing inspiration from the efficient tagging mechanism employed by Amazon S3.

In Amazon S3, tags are implemented as simple key-value pairs, where each tag consists of a Key (tag name) and a Value (assigned value). The flexibility allows up to 10 tags per S3 object, providing a versatile approach to metadata organization.[ Amazon S3 Object Tagging Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-tagging.html)

### Sample Request

The proposal should include examples of query types and expected response formats.

- Retrieve all tags for a specific bucket/object

The following request returns the tag set of the specified object.
```
GET /example-object?tagging HTTP/1.1

      Host: examplebucket.xxx

      Date: Thu, 22 Sep 2016 21:33:08 GMT

      Authorization: authorization string
```
This example illustrates one usage of GetObjectTagging.

```xml
 HTTP/1.1 200 OK

      Date: Thu, 22 Sep 2016 21:33:08 GMT

      Connection: close

      Server: AmazonS3

      <?xml version="1.0" encoding="UTF-8"?>

      <Tagging xmlns="http://s3.amazonaws.com/doc/2006-03-01/">

        <TagSet>

         <Tag>

          <Key>tag1</Key>

          <Value>val1</Value>

        </Tag>

        <Tag>

          <Key>tag2</Key>

          <Value>val2</Value>

         </Tag>

       </TagSet>

      </Tagging>
```

- Querying buckets/objects based on tags.

The following request returns the bucket/object IDs that contain the specified tag


```
GET /object?tag=xxx-xxx HTTP/1.1

      Host: xxx

      Date: Thu, 22 Sep 2016 21:33:08 GMT

      Authorization: authorization string
```



Sample Response

This example illustrates one usage of GetObjectByTagging.
```xml
  HTTP/1.1 200 OK

      Date: Thu, 22 Sep 2016 21:33:08 GMT

      Connection: close

      Server: AmazonS3

      <?xml version="1.0" encoding="UTF-8"?>

       <ObjectList>

        <Object>

         <ID>test1</ID>

         <ObjectName>vbewrz1</ObjectName>

       </Object>

       <Object>

         <ID>test2</ID>

         <ObjectName>vbewrz2</ObjectName>

       </Object>

      </ObjectList>
```
- Offering a GraphQL query method to search for resources based on tags.
```javascript
const queryObject = {

  query:

  `{

    objects (

      tags: [

       {

          name: "Type",

          values: ["manifest"]

        }

      ]

    ) {

      edges {

        node {

          id

        }

      }

    }

  }`

};

const results = await arweave.api.post('/graphql', queryObject);
```

## Challenge: Developing a High-Performance Multipart Storage Solution on Greenfield

### Main Objectives/Goals:

Greenfield, as a storage chain, traditionally depends on a Primary Storage Provider (SP) for file uploads and downloads. While Greenfield offers robust performance, it's currently constrained by the limitations of a single SP, especially noticeable when managing large files.

Taking inspiration from Amazon S3's Multipart upload feature (detailed [here](https://docs.aws.amazon.com/AmazonS3/latest/userguide/mpuoverview.html)), we envision a similar functionality for Greenfield. Users can split large files into parts, storing or retrieving them via different SPs for parallel processing efficiency. However, Greenfield presents a unique challenge: each user's bucket is linked to a specific Primary SP. Implementing Multipart functionality will require users to manage multiple buckets, each storing different file segments under defined protocols. The retrieval process will involve assembling these parts from various SPs back into the original file.

1. **Define a Client-Side Multipart Specification**: Outline a comprehensive protocol for handling multipart storage on Greenfield, considering the network's existing infrastructure of multiple SPs .
2. **Develop an Open-Source Multipart SDK**: Create a toolkit that eases the integration process for developers, ensuring a smooth implementation of the Multipart functionality in applications.


### Challenge Description:

Our goal is to harness the collective capacity of the Greenfield SP network to expedite data access, particularly for large files. The envisioned Multipart solution should align with these key criteria:

* **User-Friendly API**: The solution's API should be intuitive and straightforward, enabling developers to easily incorporate it into their applications.
* **Compatibility with Greenfield's Infrastructure**: The Multipart solution should be designed atop Greenfield's existing storage framework, necessitating minimal alterations to the current system.
* **High Performance and Reliability**: By leveraging multiple SPs, the solution must offer enhanced performance and efficiency. It should also be resilient, capable of managing network transmission errors and maintaining robust operation.