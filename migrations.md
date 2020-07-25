# customers

{
  name: 'id',
    type: 'uuid',
      isPrimary: true,
        generationStrategy: 'uuid',
    default: 'uuid_generate_v4()',
},

{
  name: 'name',
    type: 'varchar',
},

{
  name: 'email',
    type: 'varchar',
      isUnique: true,
},

{
  name: 'created_at',
    type: 'timestamp',
    default: 'now()',
},

{
  name: 'updated_at',
    type: 'timestamp',
    default: 'now()',
},

# products

{
  name: 'id',
    type: 'uuid',
      isPrimary: true,
        generationStrategy: 'uuid',
    default: 'uuid_generate_v4()',
},

{
  name: 'name',
    type: 'varchar',
      isUnique: true,
},

{
  name: 'price',
    type: 'decimal',
      precision: 6,
        scale: 2,
},

{
  name: 'quantity',
    type: 'integer',
},

{
  name: 'created_at',
    type: 'timestamp',
    default: 'now()',
},

{
  name: 'updated_at',
    type: 'timestamp',
    default: 'now()',
},

# orders

{
  name: 'id',
    type: 'uuid',
      isPrimary: true,
        generationStrategy: 'uuid',
    default: 'uuid_generate_v4()',
},

{
  name: 'cusotmer_id',
    type: 'uuid',
},


{
  name: 'created_at',
    type: 'timestamp',
    default: 'now()',
},

{
  name: 'updated_at',
    type: 'timestamp',
    default: 'now()',
},
foreingKeys: [
  {
    name: 'OrderCustomer',
    referencedTableName: 'customers',
    referencedColumnNames: ['id'],
    columnNames: ['customer_id'],
    onDelete: 'SET NULL',
    onUpdate: 'CASCADE',
  }
]

# orders_products
{
  name: 'id',
    type: 'uuid',
      isPrimary: true,
        generationStrategy: 'uuid',
    default: 'uuid_generate_v4()',
},

{
  name: 'product_id',
    type: 'uuid',
},

{
  name: 'price',
    type: 'decimal',
      precision: 6,
        scale: 2,
},

{
  name: 'quantity',
    type: 'integer',
},

{
  name: 'created_at',
    type: 'timestamp',
    default: 'now()',
},

{
  name: 'updated_at',
    type: 'timestamp',
    default: 'now()',
},
foreignKeys: [
  {
    name: 'OrderProduct-Product',
    referencedTableName: 'products',
    referencedColumnNames: ['id'],
    columnNames: ['product_id'],
    onDelete: 'SET NULL',
    onUpdate: 'CASCADE',
  },
  {
    name: 'OrderProduct-Order',
    referencedTableName: 'orders',
    referencedColumnNames: ['id'],
    columnNames: ['order_id'],
    onDelete: 'CASCADE',
    onUpdate: 'CASCADE',
  },
]
