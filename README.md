# json-bhm
JSON Business Hypermedia

A JSON based hypermedia specification aimed at working with an entity graph, with a particular focus on:

1) Metadata Context
2) Verifiable Correctness
3) Versioning
4) Domain object relationships

Inspired by Siren https://github.com/kevinswiber/siren & JSON-LD http://json-ld.org/

{  
   "context":{  
      "class":"invoice",
      "version":"2.0",
      "published":"2016-08-14T17:51:51Z",
      "author":"developer_name",
      "contact":"developer_name@mycompany.com",
      "checksums":{  
         "context":"223c1949fd01e330552772393e426d8c",
         "properties":"3a4c0dae90177ebc2c779fd6058dff59",
         "entities":"5cc514fa768f134d75e57af5edc67ab0",
         "operations":"aa03c61d4764dc6db3224e807a039f7a"
      },
      "versions":{  
         "2.0":"current",
         "1.1":"available",
         "1.0":"deprecated"
      }
   },
   "properties":{  
      "invoieNumber":"483",
      "invoiceDate":"2016-08-12T13:21:54Z",
      "name":"Hardware Invoice",
      "total":"102.33",
      "currency":"USD"
   },
   "entities":[  
      {  
         "class":[  
            "customer"
         ],
         "rel":[  
            "http://mycompany.com/rels/invoice_customers"
         ],
         "path":"http://mycompany.com/customers/7754",
         "properties":{  
            "customerID":7754
         }
      }
   ],
   "operations":{  
      "add-item":{  
         "title":"Add Item",
         "method":"POST",
         "href":"http://mycompany.com/invoices/483/items",
         "type":"application/x-www-form-urlencoded",
         "fields":[  
            {  
               "name":"orderNumber",
               "type":"hidden",
               "value":"100",
               "example":32
            },
            {  
               "name":"productCode",
               "type":"text",
               "example":"SKU1234_Hard_Drive"
            },
            {  
               "name":"quantity",
               "type":"number",
               "example":12
            }
         ]
      },
      "delete-item":{  
         "title":"Delete Item",
         "method":"POST",
         "href":"http://mycompany.com/invoices/483/items",
         "type":"application/x-www-form-urlencoded",
         "fields":[  
            {  
               "name":"orderNumber",
               "type":"hidden",
               "value":"34",
               "example":32
            },
            {  
               "name":"productCode",
               "type":"text",
               "example":"SKU444_Processors"
            },
            {  
               "name":"quantity",
               "type":"number",
               "example":75
            }
         ]
      }
   }
}
