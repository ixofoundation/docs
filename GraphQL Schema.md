```graphql
"""Exposes a URL that specifies the behaviour of this scalar."""
directive @specifiedBy(
  """The URL that specifies the behaviour of this scalar."""
  url: String!
) on SCALAR

"""
A floating point number that requires more precision than IEEE 754 binary 64
"""
scalar BigFloat

"""
A filter to be used against BigFloat fields. All fields are combined with a logical ‘and.’
"""
input BigFloatFilter {
  """
  Is null (if `true` is specified) or is not null (if `false` is specified).
  """
  isNull: Boolean

  """Equal to the specified value."""
  equalTo: BigFloat

  """Not equal to the specified value."""
  notEqualTo: BigFloat

  """
  Not equal to the specified value, treating null like an ordinary value.
  """
  distinctFrom: BigFloat

  """Equal to the specified value, treating null like an ordinary value."""
  notDistinctFrom: BigFloat

  """Included in the specified list."""
  in: [BigFloat!]

  """Not included in the specified list."""
  notIn: [BigFloat!]

  """Less than the specified value."""
  lessThan: BigFloat

  """Less than or equal to the specified value."""
  lessThanOrEqualTo: BigFloat

  """Greater than the specified value."""
  greaterThan: BigFloat

  """Greater than or equal to the specified value."""
  greaterThanOrEqualTo: BigFloat
}

"""
A signed eight-byte integer. The upper big integer values are greater than the
max value for a JavaScript number. Therefore all big integers will be output as
strings and not numbers.
"""
scalar BigInt

"""
A filter to be used against BigInt fields. All fields are combined with a logical ‘and.’
"""
input BigIntFilter {
  """
  Is null (if `true` is specified) or is not null (if `false` is specified).
  """
  isNull: Boolean

  """Equal to the specified value."""
  equalTo: BigInt

  """Not equal to the specified value."""
  notEqualTo: BigInt

  """
  Not equal to the specified value, treating null like an ordinary value.
  """
  distinctFrom: BigInt

  """Equal to the specified value, treating null like an ordinary value."""
  notDistinctFrom: BigInt

  """Included in the specified list."""
  in: [BigInt!]

  """Not included in the specified list."""
  notIn: [BigInt!]

  """Less than the specified value."""
  lessThan: BigInt

  """Less than or equal to the specified value."""
  lessThanOrEqualTo: BigInt

  """Greater than the specified value."""
  greaterThan: BigInt

  """Greater than or equal to the specified value."""
  greaterThanOrEqualTo: BigInt
}

type Bond implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  bondDid: String!
  state: String!
  token: String!
  name: String!
  description: String!
  functionType: String!
  functionParameters: JSON!
  creatorDid: String!
  controllerDid: String!
  reserveTokens: [String]
  txFeePercentage: String!
  exitFeePercentage: String!
  feeAddress: String!
  reserveWithdrawalAddress: String!
  maxSupply: JSON
  orderQuantityLimits: JSON!
  sanityRate: String!
  sanityMarginPercentage: String!
  currentSupply: JSON
  currentReserve: JSON!
  availableReserve: JSON!
  currentOutcomePaymentReserve: JSON!
  allowSells: Boolean!
  allowReserveWithdrawals: Boolean!
  alphaBond: Boolean!
  batchBlocks: String!
  outcomePayment: String!
  oracleDid: String!

  """Reads and enables pagination through a set of `BondBuy`."""
  bondBuysByBondDid(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `BondBuy`."""
    orderBy: [BondBuysOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: BondBuyCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: BondBuyFilter
  ): BondBuysConnection!

  """Reads and enables pagination through a set of `BondSell`."""
  bondSellsByBondDid(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `BondSell`."""
    orderBy: [BondSellsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: BondSellCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: BondSellFilter
  ): BondSellsConnection!

  """Reads and enables pagination through a set of `BondSwap`."""
  bondSwapsByBondDid(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `BondSwap`."""
    orderBy: [BondSwapsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: BondSwapCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: BondSwapFilter
  ): BondSwapsConnection!

  """Reads and enables pagination through a set of `ReserveWithdrawal`."""
  reserveWithdrawalsByBondDid(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `ReserveWithdrawal`."""
    orderBy: [ReserveWithdrawalsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: ReserveWithdrawalCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: ReserveWithdrawalFilter
  ): ReserveWithdrawalsConnection!

  """Reads and enables pagination through a set of `ShareWithdrawal`."""
  shareWithdrawalsByBondDid(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `ShareWithdrawal`."""
    orderBy: [ShareWithdrawalsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: ShareWithdrawalCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: ShareWithdrawalFilter
  ): ShareWithdrawalsConnection!

  """Reads and enables pagination through a set of `OutcomePayment`."""
  outcomePaymentsByBondDid(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `OutcomePayment`."""
    orderBy: [OutcomePaymentsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: OutcomePaymentCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: OutcomePaymentFilter
  ): OutcomePaymentsConnection!

  """Reads and enables pagination through a set of `BondAlpha`."""
  bondAlphasByBondDid(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `BondAlpha`."""
    orderBy: [BondAlphasOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: BondAlphaCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: BondAlphaFilter
  ): BondAlphasConnection!
}

type BondAlpha implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  id: Int!
  bondDid: String!
  alpha: String!
  oracleDid: String!
  height: Int!
  timestamp: Datetime!

  """Reads a single `Bond` that is related to this `BondAlpha`."""
  bondByBondDid: Bond
}

"""
A condition to be used against `BondAlpha` object types. All fields are tested
for equality and combined with a logical ‘and.’
"""
input BondAlphaCondition {
  """Checks for equality with the object’s `id` field."""
  id: Int

  """Checks for equality with the object’s `bondDid` field."""
  bondDid: String

  """Checks for equality with the object’s `alpha` field."""
  alpha: String

  """Checks for equality with the object’s `oracleDid` field."""
  oracleDid: String

  """Checks for equality with the object’s `height` field."""
  height: Int

  """Checks for equality with the object’s `timestamp` field."""
  timestamp: Datetime
}

"""
A filter to be used against `BondAlpha` object types. All fields are combined with a logical ‘and.’
"""
input BondAlphaFilter {
  """Filter by the object’s `id` field."""
  id: IntFilter

  """Filter by the object’s `bondDid` field."""
  bondDid: StringFilter

  """Filter by the object’s `alpha` field."""
  alpha: StringFilter

  """Filter by the object’s `oracleDid` field."""
  oracleDid: StringFilter

  """Filter by the object’s `height` field."""
  height: IntFilter

  """Filter by the object’s `timestamp` field."""
  timestamp: DatetimeFilter

  """Filter by the object’s `bondByBondDid` relation."""
  bondByBondDid: BondFilter

  """Checks for all expressions in this list."""
  and: [BondAlphaFilter!]

  """Checks for any expressions in this list."""
  or: [BondAlphaFilter!]

  """Negates the expression."""
  not: BondAlphaFilter
}

"""A connection to a list of `BondAlpha` values."""
type BondAlphasConnection {
  """A list of `BondAlpha` objects."""
  nodes: [BondAlpha!]!

  """
  A list of edges which contains the `BondAlpha` and cursor to aid in pagination.
  """
  edges: [BondAlphasEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `BondAlpha` you could get from the connection."""
  totalCount: Int!
}

"""A `BondAlpha` edge in the connection."""
type BondAlphasEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `BondAlpha` at the end of the edge."""
  node: BondAlpha!
}

"""Methods to use when ordering `BondAlpha`."""
enum BondAlphasOrderBy {
  NATURAL
  ID_ASC
  ID_DESC
  BOND_DID_ASC
  BOND_DID_DESC
  ALPHA_ASC
  ALPHA_DESC
  ORACLE_DID_ASC
  ORACLE_DID_DESC
  HEIGHT_ASC
  HEIGHT_DESC
  TIMESTAMP_ASC
  TIMESTAMP_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

type BondBuy implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  id: Int!
  bondDid: String!
  accountDid: String!
  amount: JSON!
  maxPrices: JSON!
  height: Int!
  timestamp: Datetime!

  """Reads a single `Bond` that is related to this `BondBuy`."""
  bondByBondDid: Bond
}

"""
A condition to be used against `BondBuy` object types. All fields are tested for equality and combined with a logical ‘and.’
"""
input BondBuyCondition {
  """Checks for equality with the object’s `id` field."""
  id: Int

  """Checks for equality with the object’s `bondDid` field."""
  bondDid: String

  """Checks for equality with the object’s `accountDid` field."""
  accountDid: String

  """Checks for equality with the object’s `amount` field."""
  amount: JSON

  """Checks for equality with the object’s `maxPrices` field."""
  maxPrices: JSON

  """Checks for equality with the object’s `height` field."""
  height: Int

  """Checks for equality with the object’s `timestamp` field."""
  timestamp: Datetime
}

"""
A filter to be used against `BondBuy` object types. All fields are combined with a logical ‘and.’
"""
input BondBuyFilter {
  """Filter by the object’s `id` field."""
  id: IntFilter

  """Filter by the object’s `bondDid` field."""
  bondDid: StringFilter

  """Filter by the object’s `accountDid` field."""
  accountDid: StringFilter

  """Filter by the object’s `amount` field."""
  amount: JSONFilter

  """Filter by the object’s `maxPrices` field."""
  maxPrices: JSONFilter

  """Filter by the object’s `height` field."""
  height: IntFilter

  """Filter by the object’s `timestamp` field."""
  timestamp: DatetimeFilter

  """Filter by the object’s `bondByBondDid` relation."""
  bondByBondDid: BondFilter

  """Checks for all expressions in this list."""
  and: [BondBuyFilter!]

  """Checks for any expressions in this list."""
  or: [BondBuyFilter!]

  """Negates the expression."""
  not: BondBuyFilter
}

"""A connection to a list of `BondBuy` values."""
type BondBuysConnection {
  """A list of `BondBuy` objects."""
  nodes: [BondBuy!]!

  """
  A list of edges which contains the `BondBuy` and cursor to aid in pagination.
  """
  edges: [BondBuysEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `BondBuy` you could get from the connection."""
  totalCount: Int!
}

"""A `BondBuy` edge in the connection."""
type BondBuysEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `BondBuy` at the end of the edge."""
  node: BondBuy!
}

"""Methods to use when ordering `BondBuy`."""
enum BondBuysOrderBy {
  NATURAL
  ID_ASC
  ID_DESC
  BOND_DID_ASC
  BOND_DID_DESC
  ACCOUNT_DID_ASC
  ACCOUNT_DID_DESC
  AMOUNT_ASC
  AMOUNT_DESC
  MAX_PRICES_ASC
  MAX_PRICES_DESC
  HEIGHT_ASC
  HEIGHT_DESC
  TIMESTAMP_ASC
  TIMESTAMP_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

"""
A condition to be used against `Bond` object types. All fields are tested for equality and combined with a logical ‘and.’
"""
input BondCondition {
  """Checks for equality with the object’s `bondDid` field."""
  bondDid: String

  """Checks for equality with the object’s `state` field."""
  state: String

  """Checks for equality with the object’s `token` field."""
  token: String

  """Checks for equality with the object’s `name` field."""
  name: String

  """Checks for equality with the object’s `description` field."""
  description: String

  """Checks for equality with the object’s `functionType` field."""
  functionType: String

  """Checks for equality with the object’s `functionParameters` field."""
  functionParameters: JSON

  """Checks for equality with the object’s `creatorDid` field."""
  creatorDid: String

  """Checks for equality with the object’s `controllerDid` field."""
  controllerDid: String

  """Checks for equality with the object’s `reserveTokens` field."""
  reserveTokens: [String]

  """Checks for equality with the object’s `txFeePercentage` field."""
  txFeePercentage: String

  """Checks for equality with the object’s `exitFeePercentage` field."""
  exitFeePercentage: String

  """Checks for equality with the object’s `feeAddress` field."""
  feeAddress: String

  """
  Checks for equality with the object’s `reserveWithdrawalAddress` field.
  """
  reserveWithdrawalAddress: String

  """Checks for equality with the object’s `maxSupply` field."""
  maxSupply: JSON

  """Checks for equality with the object’s `orderQuantityLimits` field."""
  orderQuantityLimits: JSON

  """Checks for equality with the object’s `sanityRate` field."""
  sanityRate: String

  """Checks for equality with the object’s `sanityMarginPercentage` field."""
  sanityMarginPercentage: String

  """Checks for equality with the object’s `currentSupply` field."""
  currentSupply: JSON

  """Checks for equality with the object’s `currentReserve` field."""
  currentReserve: JSON

  """Checks for equality with the object’s `availableReserve` field."""
  availableReserve: JSON

  """
  Checks for equality with the object’s `currentOutcomePaymentReserve` field.
  """
  currentOutcomePaymentReserve: JSON

  """Checks for equality with the object’s `allowSells` field."""
  allowSells: Boolean

  """Checks for equality with the object’s `allowReserveWithdrawals` field."""
  allowReserveWithdrawals: Boolean

  """Checks for equality with the object’s `alphaBond` field."""
  alphaBond: Boolean

  """Checks for equality with the object’s `batchBlocks` field."""
  batchBlocks: String

  """Checks for equality with the object’s `outcomePayment` field."""
  outcomePayment: String

  """Checks for equality with the object’s `oracleDid` field."""
  oracleDid: String
}

"""
A filter to be used against `Bond` object types. All fields are combined with a logical ‘and.’
"""
input BondFilter {
  """Filter by the object’s `bondDid` field."""
  bondDid: StringFilter

  """Filter by the object’s `state` field."""
  state: StringFilter

  """Filter by the object’s `token` field."""
  token: StringFilter

  """Filter by the object’s `name` field."""
  name: StringFilter

  """Filter by the object’s `description` field."""
  description: StringFilter

  """Filter by the object’s `functionType` field."""
  functionType: StringFilter

  """Filter by the object’s `functionParameters` field."""
  functionParameters: JSONFilter

  """Filter by the object’s `creatorDid` field."""
  creatorDid: StringFilter

  """Filter by the object’s `controllerDid` field."""
  controllerDid: StringFilter

  """Filter by the object’s `reserveTokens` field."""
  reserveTokens: StringListFilter

  """Filter by the object’s `txFeePercentage` field."""
  txFeePercentage: StringFilter

  """Filter by the object’s `exitFeePercentage` field."""
  exitFeePercentage: StringFilter

  """Filter by the object’s `feeAddress` field."""
  feeAddress: StringFilter

  """Filter by the object’s `reserveWithdrawalAddress` field."""
  reserveWithdrawalAddress: StringFilter

  """Filter by the object’s `maxSupply` field."""
  maxSupply: JSONFilter

  """Filter by the object’s `orderQuantityLimits` field."""
  orderQuantityLimits: JSONFilter

  """Filter by the object’s `sanityRate` field."""
  sanityRate: StringFilter

  """Filter by the object’s `sanityMarginPercentage` field."""
  sanityMarginPercentage: StringFilter

  """Filter by the object’s `currentSupply` field."""
  currentSupply: JSONFilter

  """Filter by the object’s `currentReserve` field."""
  currentReserve: JSONFilter

  """Filter by the object’s `availableReserve` field."""
  availableReserve: JSONFilter

  """Filter by the object’s `currentOutcomePaymentReserve` field."""
  currentOutcomePaymentReserve: JSONFilter

  """Filter by the object’s `allowSells` field."""
  allowSells: BooleanFilter

  """Filter by the object’s `allowReserveWithdrawals` field."""
  allowReserveWithdrawals: BooleanFilter

  """Filter by the object’s `alphaBond` field."""
  alphaBond: BooleanFilter

  """Filter by the object’s `batchBlocks` field."""
  batchBlocks: StringFilter

  """Filter by the object’s `outcomePayment` field."""
  outcomePayment: StringFilter

  """Filter by the object’s `oracleDid` field."""
  oracleDid: StringFilter

  """Filter by the object’s `bondBuysByBondDid` relation."""
  bondBuysByBondDid: BondToManyBondBuyFilter

  """Some related `bondBuysByBondDid` exist."""
  bondBuysByBondDidExist: Boolean

  """Filter by the object’s `bondSellsByBondDid` relation."""
  bondSellsByBondDid: BondToManyBondSellFilter

  """Some related `bondSellsByBondDid` exist."""
  bondSellsByBondDidExist: Boolean

  """Filter by the object’s `bondSwapsByBondDid` relation."""
  bondSwapsByBondDid: BondToManyBondSwapFilter

  """Some related `bondSwapsByBondDid` exist."""
  bondSwapsByBondDidExist: Boolean

  """Filter by the object’s `reserveWithdrawalsByBondDid` relation."""
  reserveWithdrawalsByBondDid: BondToManyReserveWithdrawalFilter

  """Some related `reserveWithdrawalsByBondDid` exist."""
  reserveWithdrawalsByBondDidExist: Boolean

  """Filter by the object’s `shareWithdrawalsByBondDid` relation."""
  shareWithdrawalsByBondDid: BondToManyShareWithdrawalFilter

  """Some related `shareWithdrawalsByBondDid` exist."""
  shareWithdrawalsByBondDidExist: Boolean

  """Filter by the object’s `outcomePaymentsByBondDid` relation."""
  outcomePaymentsByBondDid: BondToManyOutcomePaymentFilter

  """Some related `outcomePaymentsByBondDid` exist."""
  outcomePaymentsByBondDidExist: Boolean

  """Filter by the object’s `bondAlphasByBondDid` relation."""
  bondAlphasByBondDid: BondToManyBondAlphaFilter

  """Some related `bondAlphasByBondDid` exist."""
  bondAlphasByBondDidExist: Boolean

  """Checks for all expressions in this list."""
  and: [BondFilter!]

  """Checks for any expressions in this list."""
  or: [BondFilter!]

  """Negates the expression."""
  not: BondFilter
}

"""A connection to a list of `Bond` values."""
type BondsConnection {
  """A list of `Bond` objects."""
  nodes: [Bond!]!

  """
  A list of edges which contains the `Bond` and cursor to aid in pagination.
  """
  edges: [BondsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `Bond` you could get from the connection."""
  totalCount: Int!
}

"""A `Bond` edge in the connection."""
type BondsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `Bond` at the end of the edge."""
  node: Bond!
}

type BondSell implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  id: Int!
  bondDid: String!
  accountDid: String!
  amount: JSON!
  height: Int!
  timestamp: Datetime!

  """Reads a single `Bond` that is related to this `BondSell`."""
  bondByBondDid: Bond
}

"""
A condition to be used against `BondSell` object types. All fields are tested
for equality and combined with a logical ‘and.’
"""
input BondSellCondition {
  """Checks for equality with the object’s `id` field."""
  id: Int

  """Checks for equality with the object’s `bondDid` field."""
  bondDid: String

  """Checks for equality with the object’s `accountDid` field."""
  accountDid: String

  """Checks for equality with the object’s `amount` field."""
  amount: JSON

  """Checks for equality with the object’s `height` field."""
  height: Int

  """Checks for equality with the object’s `timestamp` field."""
  timestamp: Datetime
}

"""
A filter to be used against `BondSell` object types. All fields are combined with a logical ‘and.’
"""
input BondSellFilter {
  """Filter by the object’s `id` field."""
  id: IntFilter

  """Filter by the object’s `bondDid` field."""
  bondDid: StringFilter

  """Filter by the object’s `accountDid` field."""
  accountDid: StringFilter

  """Filter by the object’s `amount` field."""
  amount: JSONFilter

  """Filter by the object’s `height` field."""
  height: IntFilter

  """Filter by the object’s `timestamp` field."""
  timestamp: DatetimeFilter

  """Filter by the object’s `bondByBondDid` relation."""
  bondByBondDid: BondFilter

  """Checks for all expressions in this list."""
  and: [BondSellFilter!]

  """Checks for any expressions in this list."""
  or: [BondSellFilter!]

  """Negates the expression."""
  not: BondSellFilter
}

"""A connection to a list of `BondSell` values."""
type BondSellsConnection {
  """A list of `BondSell` objects."""
  nodes: [BondSell!]!

  """
  A list of edges which contains the `BondSell` and cursor to aid in pagination.
  """
  edges: [BondSellsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `BondSell` you could get from the connection."""
  totalCount: Int!
}

"""A `BondSell` edge in the connection."""
type BondSellsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `BondSell` at the end of the edge."""
  node: BondSell!
}

"""Methods to use when ordering `BondSell`."""
enum BondSellsOrderBy {
  NATURAL
  ID_ASC
  ID_DESC
  BOND_DID_ASC
  BOND_DID_DESC
  ACCOUNT_DID_ASC
  ACCOUNT_DID_DESC
  AMOUNT_ASC
  AMOUNT_DESC
  HEIGHT_ASC
  HEIGHT_DESC
  TIMESTAMP_ASC
  TIMESTAMP_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

"""Methods to use when ordering `Bond`."""
enum BondsOrderBy {
  NATURAL
  BOND_DID_ASC
  BOND_DID_DESC
  STATE_ASC
  STATE_DESC
  TOKEN_ASC
  TOKEN_DESC
  NAME_ASC
  NAME_DESC
  DESCRIPTION_ASC
  DESCRIPTION_DESC
  FUNCTION_TYPE_ASC
  FUNCTION_TYPE_DESC
  FUNCTION_PARAMETERS_ASC
  FUNCTION_PARAMETERS_DESC
  CREATOR_DID_ASC
  CREATOR_DID_DESC
  CONTROLLER_DID_ASC
  CONTROLLER_DID_DESC
  RESERVE_TOKENS_ASC
  RESERVE_TOKENS_DESC
  TX_FEE_PERCENTAGE_ASC
  TX_FEE_PERCENTAGE_DESC
  EXIT_FEE_PERCENTAGE_ASC
  EXIT_FEE_PERCENTAGE_DESC
  FEE_ADDRESS_ASC
  FEE_ADDRESS_DESC
  RESERVE_WITHDRAWAL_ADDRESS_ASC
  RESERVE_WITHDRAWAL_ADDRESS_DESC
  MAX_SUPPLY_ASC
  MAX_SUPPLY_DESC
  ORDER_QUANTITY_LIMITS_ASC
  ORDER_QUANTITY_LIMITS_DESC
  SANITY_RATE_ASC
  SANITY_RATE_DESC
  SANITY_MARGIN_PERCENTAGE_ASC
  SANITY_MARGIN_PERCENTAGE_DESC
  CURRENT_SUPPLY_ASC
  CURRENT_SUPPLY_DESC
  CURRENT_RESERVE_ASC
  CURRENT_RESERVE_DESC
  AVAILABLE_RESERVE_ASC
  AVAILABLE_RESERVE_DESC
  CURRENT_OUTCOME_PAYMENT_RESERVE_ASC
  CURRENT_OUTCOME_PAYMENT_RESERVE_DESC
  ALLOW_SELLS_ASC
  ALLOW_SELLS_DESC
  ALLOW_RESERVE_WITHDRAWALS_ASC
  ALLOW_RESERVE_WITHDRAWALS_DESC
  ALPHA_BOND_ASC
  ALPHA_BOND_DESC
  BATCH_BLOCKS_ASC
  BATCH_BLOCKS_DESC
  OUTCOME_PAYMENT_ASC
  OUTCOME_PAYMENT_DESC
  ORACLE_DID_ASC
  ORACLE_DID_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

type BondSwap implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  id: Int!
  bondDid: String!
  accountDid: String!
  amount: JSON!
  toToken: String!
  height: Int!
  timestamp: Datetime!

  """Reads a single `Bond` that is related to this `BondSwap`."""
  bondByBondDid: Bond
}

"""
A condition to be used against `BondSwap` object types. All fields are tested
for equality and combined with a logical ‘and.’
"""
input BondSwapCondition {
  """Checks for equality with the object’s `id` field."""
  id: Int

  """Checks for equality with the object’s `bondDid` field."""
  bondDid: String

  """Checks for equality with the object’s `accountDid` field."""
  accountDid: String

  """Checks for equality with the object’s `amount` field."""
  amount: JSON

  """Checks for equality with the object’s `toToken` field."""
  toToken: String

  """Checks for equality with the object’s `height` field."""
  height: Int

  """Checks for equality with the object’s `timestamp` field."""
  timestamp: Datetime
}

"""
A filter to be used against `BondSwap` object types. All fields are combined with a logical ‘and.’
"""
input BondSwapFilter {
  """Filter by the object’s `id` field."""
  id: IntFilter

  """Filter by the object’s `bondDid` field."""
  bondDid: StringFilter

  """Filter by the object’s `accountDid` field."""
  accountDid: StringFilter

  """Filter by the object’s `amount` field."""
  amount: JSONFilter

  """Filter by the object’s `toToken` field."""
  toToken: StringFilter

  """Filter by the object’s `height` field."""
  height: IntFilter

  """Filter by the object’s `timestamp` field."""
  timestamp: DatetimeFilter

  """Filter by the object’s `bondByBondDid` relation."""
  bondByBondDid: BondFilter

  """Checks for all expressions in this list."""
  and: [BondSwapFilter!]

  """Checks for any expressions in this list."""
  or: [BondSwapFilter!]

  """Negates the expression."""
  not: BondSwapFilter
}

"""A connection to a list of `BondSwap` values."""
type BondSwapsConnection {
  """A list of `BondSwap` objects."""
  nodes: [BondSwap!]!

  """
  A list of edges which contains the `BondSwap` and cursor to aid in pagination.
  """
  edges: [BondSwapsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `BondSwap` you could get from the connection."""
  totalCount: Int!
}

"""A `BondSwap` edge in the connection."""
type BondSwapsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `BondSwap` at the end of the edge."""
  node: BondSwap!
}

"""Methods to use when ordering `BondSwap`."""
enum BondSwapsOrderBy {
  NATURAL
  ID_ASC
  ID_DESC
  BOND_DID_ASC
  BOND_DID_DESC
  ACCOUNT_DID_ASC
  ACCOUNT_DID_DESC
  AMOUNT_ASC
  AMOUNT_DESC
  TO_TOKEN_ASC
  TO_TOKEN_DESC
  HEIGHT_ASC
  HEIGHT_DESC
  TIMESTAMP_ASC
  TIMESTAMP_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

"""
A filter to be used against many `BondAlpha` object types. All fields are combined with a logical ‘and.’
"""
input BondToManyBondAlphaFilter {
  """
  Every related `BondAlpha` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: BondAlphaFilter

  """
  Some related `BondAlpha` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: BondAlphaFilter

  """
  No related `BondAlpha` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: BondAlphaFilter
}

"""
A filter to be used against many `BondBuy` object types. All fields are combined with a logical ‘and.’
"""
input BondToManyBondBuyFilter {
  """
  Every related `BondBuy` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: BondBuyFilter

  """
  Some related `BondBuy` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: BondBuyFilter

  """
  No related `BondBuy` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: BondBuyFilter
}

"""
A filter to be used against many `BondSell` object types. All fields are combined with a logical ‘and.’
"""
input BondToManyBondSellFilter {
  """
  Every related `BondSell` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: BondSellFilter

  """
  Some related `BondSell` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: BondSellFilter

  """
  No related `BondSell` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: BondSellFilter
}

"""
A filter to be used against many `BondSwap` object types. All fields are combined with a logical ‘and.’
"""
input BondToManyBondSwapFilter {
  """
  Every related `BondSwap` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: BondSwapFilter

  """
  Some related `BondSwap` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: BondSwapFilter

  """
  No related `BondSwap` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: BondSwapFilter
}

"""
A filter to be used against many `OutcomePayment` object types. All fields are combined with a logical ‘and.’
"""
input BondToManyOutcomePaymentFilter {
  """
  Every related `OutcomePayment` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: OutcomePaymentFilter

  """
  Some related `OutcomePayment` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: OutcomePaymentFilter

  """
  No related `OutcomePayment` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: OutcomePaymentFilter
}

"""
A filter to be used against many `ReserveWithdrawal` object types. All fields are combined with a logical ‘and.’
"""
input BondToManyReserveWithdrawalFilter {
  """
  Every related `ReserveWithdrawal` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: ReserveWithdrawalFilter

  """
  Some related `ReserveWithdrawal` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: ReserveWithdrawalFilter

  """
  No related `ReserveWithdrawal` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: ReserveWithdrawalFilter
}

"""
A filter to be used against many `ShareWithdrawal` object types. All fields are combined with a logical ‘and.’
"""
input BondToManyShareWithdrawalFilter {
  """
  Every related `ShareWithdrawal` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: ShareWithdrawalFilter

  """
  Some related `ShareWithdrawal` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: ShareWithdrawalFilter

  """
  No related `ShareWithdrawal` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: ShareWithdrawalFilter
}

"""
A filter to be used against Boolean fields. All fields are combined with a logical ‘and.’
"""
input BooleanFilter {
  """
  Is null (if `true` is specified) or is not null (if `false` is specified).
  """
  isNull: Boolean

  """Equal to the specified value."""
  equalTo: Boolean

  """Not equal to the specified value."""
  notEqualTo: Boolean

  """
  Not equal to the specified value, treating null like an ordinary value.
  """
  distinctFrom: Boolean

  """Equal to the specified value, treating null like an ordinary value."""
  notDistinctFrom: Boolean

  """Included in the specified list."""
  in: [Boolean!]

  """Not included in the specified list."""
  notIn: [Boolean!]

  """Less than the specified value."""
  lessThan: Boolean

  """Less than or equal to the specified value."""
  lessThanOrEqualTo: Boolean

  """Greater than the specified value."""
  greaterThan: Boolean

  """Greater than or equal to the specified value."""
  greaterThanOrEqualTo: Boolean
}

type Chain implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  chainId: String!
  blockHeight: Int!
}

"""
A condition to be used against `Chain` object types. All fields are tested for equality and combined with a logical ‘and.’
"""
input ChainCondition {
  """Checks for equality with the object’s `chainId` field."""
  chainId: String

  """Checks for equality with the object’s `blockHeight` field."""
  blockHeight: Int
}

"""
A filter to be used against `Chain` object types. All fields are combined with a logical ‘and.’
"""
input ChainFilter {
  """Filter by the object’s `chainId` field."""
  chainId: StringFilter

  """Filter by the object’s `blockHeight` field."""
  blockHeight: IntFilter

  """Checks for all expressions in this list."""
  and: [ChainFilter!]

  """Checks for any expressions in this list."""
  or: [ChainFilter!]

  """Negates the expression."""
  not: ChainFilter
}

"""A connection to a list of `Chain` values."""
type ChainsConnection {
  """A list of `Chain` objects."""
  nodes: [Chain!]!

  """
  A list of edges which contains the `Chain` and cursor to aid in pagination.
  """
  edges: [ChainsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `Chain` you could get from the connection."""
  totalCount: Int!
}

"""A `Chain` edge in the connection."""
type ChainsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `Chain` at the end of the edge."""
  node: Chain!
}

"""Methods to use when ordering `Chain`."""
enum ChainsOrderBy {
  NATURAL
  CHAIN_ID_ASC
  CHAIN_ID_DESC
  BLOCK_HEIGHT_ASC
  BLOCK_HEIGHT_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

type Claim implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  claimId: String!
  agentDid: String!
  agentAddress: String!
  submissionDate: Datetime!
  paymentsStatus: JSON!
  schemaType: String
  collectionId: String!

  """Reads a single `ClaimCollection` that is related to this `Claim`."""
  collection: ClaimCollection

  """Reads a single `Evaluation` that is related to this `Claim`."""
  evaluationByClaimId: Evaluation
}

type ClaimCollection implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  id: String!
  entity: String!
  admin: String!
  protocol: String!
  startDate: Datetime
  endDate: Datetime
  quota: Int!
  count: Int!
  evaluated: Int!
  approved: Int!
  rejected: Int!
  disputed: Int!
  invalidated: Int!
  state: Int!
  payments: JSON!

  """Reads and enables pagination through a set of `Claim`."""
  claimsByCollectionId(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Claim`."""
    orderBy: [ClaimsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: ClaimCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: ClaimFilter
  ): ClaimsConnection!

  """Checks if there are any claims with null schemaType"""
  claimSchemaTypesLoaded: Boolean!
}

"""
A condition to be used against `ClaimCollection` object types. All fields are
tested for equality and combined with a logical ‘and.’
"""
input ClaimCollectionCondition {
  """Checks for equality with the object’s `id` field."""
  id: String

  """Checks for equality with the object’s `entity` field."""
  entity: String

  """Checks for equality with the object’s `admin` field."""
  admin: String

  """Checks for equality with the object’s `protocol` field."""
  protocol: String

  """Checks for equality with the object’s `startDate` field."""
  startDate: Datetime

  """Checks for equality with the object’s `endDate` field."""
  endDate: Datetime

  """Checks for equality with the object’s `quota` field."""
  quota: Int

  """Checks for equality with the object’s `count` field."""
  count: Int

  """Checks for equality with the object’s `evaluated` field."""
  evaluated: Int

  """Checks for equality with the object’s `approved` field."""
  approved: Int

  """Checks for equality with the object’s `rejected` field."""
  rejected: Int

  """Checks for equality with the object’s `disputed` field."""
  disputed: Int

  """Checks for equality with the object’s `invalidated` field."""
  invalidated: Int

  """Checks for equality with the object’s `state` field."""
  state: Int

  """Checks for equality with the object’s `payments` field."""
  payments: JSON
}

"""
A filter to be used against `ClaimCollection` object types. All fields are combined with a logical ‘and.’
"""
input ClaimCollectionFilter {
  """Filter by the object’s `id` field."""
  id: StringFilter

  """Filter by the object’s `entity` field."""
  entity: StringFilter

  """Filter by the object’s `admin` field."""
  admin: StringFilter

  """Filter by the object’s `protocol` field."""
  protocol: StringFilter

  """Filter by the object’s `startDate` field."""
  startDate: DatetimeFilter

  """Filter by the object’s `endDate` field."""
  endDate: DatetimeFilter

  """Filter by the object’s `quota` field."""
  quota: IntFilter

  """Filter by the object’s `count` field."""
  count: IntFilter

  """Filter by the object’s `evaluated` field."""
  evaluated: IntFilter

  """Filter by the object’s `approved` field."""
  approved: IntFilter

  """Filter by the object’s `rejected` field."""
  rejected: IntFilter

  """Filter by the object’s `disputed` field."""
  disputed: IntFilter

  """Filter by the object’s `invalidated` field."""
  invalidated: IntFilter

  """Filter by the object’s `state` field."""
  state: IntFilter

  """Filter by the object’s `payments` field."""
  payments: JSONFilter

  """Filter by the object’s `claimsByCollectionId` relation."""
  claimsByCollectionId: ClaimCollectionToManyClaimFilter

  """Some related `claimsByCollectionId` exist."""
  claimsByCollectionIdExist: Boolean

  """Checks for all expressions in this list."""
  and: [ClaimCollectionFilter!]

  """Checks for any expressions in this list."""
  or: [ClaimCollectionFilter!]

  """Negates the expression."""
  not: ClaimCollectionFilter
}

"""A connection to a list of `ClaimCollection` values."""
type ClaimCollectionsConnection {
  """A list of `ClaimCollection` objects."""
  nodes: [ClaimCollection!]!

  """
  A list of edges which contains the `ClaimCollection` and cursor to aid in pagination.
  """
  edges: [ClaimCollectionsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """
  The count of *all* `ClaimCollection` you could get from the connection.
  """
  totalCount: Int!
}

"""A `ClaimCollection` edge in the connection."""
type ClaimCollectionsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `ClaimCollection` at the end of the edge."""
  node: ClaimCollection!
}

"""Methods to use when ordering `ClaimCollection`."""
enum ClaimCollectionsOrderBy {
  NATURAL
  ID_ASC
  ID_DESC
  ENTITY_ASC
  ENTITY_DESC
  ADMIN_ASC
  ADMIN_DESC
  PROTOCOL_ASC
  PROTOCOL_DESC
  START_DATE_ASC
  START_DATE_DESC
  END_DATE_ASC
  END_DATE_DESC
  QUOTA_ASC
  QUOTA_DESC
  COUNT_ASC
  COUNT_DESC
  EVALUATED_ASC
  EVALUATED_DESC
  APPROVED_ASC
  APPROVED_DESC
  REJECTED_ASC
  REJECTED_DESC
  DISPUTED_ASC
  DISPUTED_DESC
  INVALIDATED_ASC
  INVALIDATED_DESC
  STATE_ASC
  STATE_DESC
  PAYMENTS_ASC
  PAYMENTS_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

"""
A filter to be used against many `Claim` object types. All fields are combined with a logical ‘and.’
"""
input ClaimCollectionToManyClaimFilter {
  """
  Every related `Claim` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: ClaimFilter

  """
  Some related `Claim` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: ClaimFilter

  """
  No related `Claim` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: ClaimFilter
}

"""
A condition to be used against `Claim` object types. All fields are tested for equality and combined with a logical ‘and.’
"""
input ClaimCondition {
  """Checks for equality with the object’s `claimId` field."""
  claimId: String

  """Checks for equality with the object’s `agentDid` field."""
  agentDid: String

  """Checks for equality with the object’s `agentAddress` field."""
  agentAddress: String

  """Checks for equality with the object’s `submissionDate` field."""
  submissionDate: Datetime

  """Checks for equality with the object’s `paymentsStatus` field."""
  paymentsStatus: JSON

  """Checks for equality with the object’s `schemaType` field."""
  schemaType: String

  """Checks for equality with the object’s `collectionId` field."""
  collectionId: String
}

"""
A filter to be used against `Claim` object types. All fields are combined with a logical ‘and.’
"""
input ClaimFilter {
  """Filter by the object’s `claimId` field."""
  claimId: StringFilter

  """Filter by the object’s `agentDid` field."""
  agentDid: StringFilter

  """Filter by the object’s `agentAddress` field."""
  agentAddress: StringFilter

  """Filter by the object’s `submissionDate` field."""
  submissionDate: DatetimeFilter

  """Filter by the object’s `paymentsStatus` field."""
  paymentsStatus: JSONFilter

  """Filter by the object’s `schemaType` field."""
  schemaType: StringFilter

  """Filter by the object’s `collectionId` field."""
  collectionId: StringFilter

  """Filter by the object’s `evaluationByClaimId` relation."""
  evaluationByClaimId: EvaluationFilter

  """A related `evaluationByClaimId` exists."""
  evaluationByClaimIdExists: Boolean

  """Filter by the object’s `collection` relation."""
  collection: ClaimCollectionFilter

  """Checks for all expressions in this list."""
  and: [ClaimFilter!]

  """Checks for any expressions in this list."""
  or: [ClaimFilter!]

  """Negates the expression."""
  not: ClaimFilter
}

"""A connection to a list of `Claim` values."""
type ClaimsConnection {
  """A list of `Claim` objects."""
  nodes: [Claim!]!

  """
  A list of edges which contains the `Claim` and cursor to aid in pagination.
  """
  edges: [ClaimsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `Claim` you could get from the connection."""
  totalCount: Int!
}

"""A `Claim` edge in the connection."""
type ClaimsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `Claim` at the end of the edge."""
  node: Claim!
}

"""Methods to use when ordering `Claim`."""
enum ClaimsOrderBy {
  NATURAL
  CLAIM_ID_ASC
  CLAIM_ID_DESC
  AGENT_DID_ASC
  AGENT_DID_DESC
  AGENT_ADDRESS_ASC
  AGENT_ADDRESS_DESC
  SUBMISSION_DATE_ASC
  SUBMISSION_DATE_DESC
  PAYMENTS_STATUS_ASC
  PAYMENTS_STATUS_DESC
  SCHEMA_TYPE_ASC
  SCHEMA_TYPE_DESC
  COLLECTION_ID_ASC
  COLLECTION_ID_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

"""A location in a connection that can be used for resuming pagination."""
scalar Cursor

"""
A point in time as described by the [ISO
8601](https://en.wikipedia.org/wiki/ISO_8601) standard. May or may not include a timezone.
"""
scalar Datetime

"""
A filter to be used against Datetime fields. All fields are combined with a logical ‘and.’
"""
input DatetimeFilter {
  """
  Is null (if `true` is specified) or is not null (if `false` is specified).
  """
  isNull: Boolean

  """Equal to the specified value."""
  equalTo: Datetime

  """Not equal to the specified value."""
  notEqualTo: Datetime

  """
  Not equal to the specified value, treating null like an ordinary value.
  """
  distinctFrom: Datetime

  """Equal to the specified value, treating null like an ordinary value."""
  notDistinctFrom: Datetime

  """Included in the specified list."""
  in: [Datetime!]

  """Not included in the specified list."""
  notIn: [Datetime!]

  """Less than the specified value."""
  lessThan: Datetime

  """Less than or equal to the specified value."""
  lessThanOrEqualTo: Datetime

  """Greater than the specified value."""
  greaterThan: Datetime

  """Greater than or equal to the specified value."""
  greaterThanOrEqualTo: Datetime
}

type Dispute implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  proof: String!
  subjectId: String!
  type: Int!
  data: JSON!
}

"""
A condition to be used against `Dispute` object types. All fields are tested for equality and combined with a logical ‘and.’
"""
input DisputeCondition {
  """Checks for equality with the object’s `proof` field."""
  proof: String

  """Checks for equality with the object’s `subjectId` field."""
  subjectId: String

  """Checks for equality with the object’s `type` field."""
  type: Int

  """Checks for equality with the object’s `data` field."""
  data: JSON
}

"""
A filter to be used against `Dispute` object types. All fields are combined with a logical ‘and.’
"""
input DisputeFilter {
  """Filter by the object’s `proof` field."""
  proof: StringFilter

  """Filter by the object’s `subjectId` field."""
  subjectId: StringFilter

  """Filter by the object’s `type` field."""
  type: IntFilter

  """Filter by the object’s `data` field."""
  data: JSONFilter

  """Checks for all expressions in this list."""
  and: [DisputeFilter!]

  """Checks for any expressions in this list."""
  or: [DisputeFilter!]

  """Negates the expression."""
  not: DisputeFilter
}

"""A connection to a list of `Dispute` values."""
type DisputesConnection {
  """A list of `Dispute` objects."""
  nodes: [Dispute!]!

  """
  A list of edges which contains the `Dispute` and cursor to aid in pagination.
  """
  edges: [DisputesEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `Dispute` you could get from the connection."""
  totalCount: Int!
}

"""A `Dispute` edge in the connection."""
type DisputesEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `Dispute` at the end of the edge."""
  node: Dispute!
}

"""Methods to use when ordering `Dispute`."""
enum DisputesOrderBy {
  NATURAL
  PROOF_ASC
  PROOF_DESC
  SUBJECT_ID_ASC
  SUBJECT_ID_DESC
  TYPE_ASC
  TYPE_DESC
  DATA_ASC
  DATA_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

"""A connection to a list of `Entity` values."""
type EntitiesConnection {
  """A list of `Entity` objects."""
  nodes: [Entity!]!

  """
  A list of edges which contains the `Entity` and cursor to aid in pagination.
  """
  edges: [EntitiesEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `Entity` you could get from the connection."""
  totalCount: Int!
}

"""A `Entity` edge in the connection."""
type EntitiesEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `Entity` at the end of the edge."""
  node: Entity!
}

"""Methods to use when ordering `Entity`."""
enum EntitiesOrderBy {
  NATURAL
  ID_ASC
  ID_DESC
  TYPE_ASC
  TYPE_DESC
  START_DATE_ASC
  START_DATE_DESC
  END_DATE_ASC
  END_DATE_DESC
  STATUS_ASC
  STATUS_DESC
  RELAYER_NODE_ASC
  RELAYER_NODE_DESC
  CREDENTIALS_ASC
  CREDENTIALS_DESC
  ENTITY_VERIFIED_ASC
  ENTITY_VERIFIED_DESC
  METADATA_ASC
  METADATA_DESC
  ACCOUNTS_ASC
  ACCOUNTS_DESC
  EXTERNAL_ID_ASC
  EXTERNAL_ID_DESC
  OWNER_ASC
  OWNER_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

type Entity implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  id: String!
  type: String!
  startDate: Datetime
  endDate: Datetime
  status: Int!
  relayerNode: String!
  credentials: [String]
  entityVerified: Boolean!
  metadata: JSON!
  accounts: JSON!
  externalId: String
  owner: String

  """Reads a single `Iid` that is related to this `Entity`."""
  iidById: Iid

  """Reads and enables pagination through a set of `TokenClass`."""
  tokenClassesByClass(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `TokenClass`."""
    orderBy: [TokenClassesOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TokenClassCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TokenClassFilter
  ): TokenClassesConnection!

  """Reads and enables pagination through a set of `Token`."""
  tokensByCollection(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Token`."""
    orderBy: [TokensOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TokenCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TokenFilter
  ): TokensConnection!
  context: JSON!
  controller: [String!]!
  verificationMethod: JSON!
  service: JSON!
  authentication: [String!]!
  assertionMethod: [String!]!
  keyAgreement: [String!]!
  capabilityInvocation: [String!]!
  capabilityDelegation: [String!]!
  linkedResource: JSON!
  linkedClaim: JSON!
  accordedRight: JSON!
  linkedEntity: JSON!
  alsoKnownAs: String!
  settings: JSON!
}

"""
A condition to be used against `Entity` object types. All fields are tested for equality and combined with a logical ‘and.’
"""
input EntityCondition {
  """Checks for equality with the object’s `id` field."""
  id: String

  """Checks for equality with the object’s `type` field."""
  type: String

  """Checks for equality with the object’s `startDate` field."""
  startDate: Datetime

  """Checks for equality with the object’s `endDate` field."""
  endDate: Datetime

  """Checks for equality with the object’s `status` field."""
  status: Int

  """Checks for equality with the object’s `relayerNode` field."""
  relayerNode: String

  """Checks for equality with the object’s `credentials` field."""
  credentials: [String]

  """Checks for equality with the object’s `entityVerified` field."""
  entityVerified: Boolean

  """Checks for equality with the object’s `metadata` field."""
  metadata: JSON

  """Checks for equality with the object’s `accounts` field."""
  accounts: JSON

  """Checks for equality with the object’s `externalId` field."""
  externalId: String

  """Checks for equality with the object’s `owner` field."""
  owner: String
}

"""
A filter to be used against `Entity` object types. All fields are combined with a logical ‘and.’
"""
input EntityFilter {
  """Filter by the object’s `id` field."""
  id: StringFilter

  """Filter by the object’s `type` field."""
  type: StringFilter

  """Filter by the object’s `startDate` field."""
  startDate: DatetimeFilter

  """Filter by the object’s `endDate` field."""
  endDate: DatetimeFilter

  """Filter by the object’s `status` field."""
  status: IntFilter

  """Filter by the object’s `relayerNode` field."""
  relayerNode: StringFilter

  """Filter by the object’s `credentials` field."""
  credentials: StringListFilter

  """Filter by the object’s `entityVerified` field."""
  entityVerified: BooleanFilter

  """Filter by the object’s `metadata` field."""
  metadata: JSONFilter

  """Filter by the object’s `accounts` field."""
  accounts: JSONFilter

  """Filter by the object’s `externalId` field."""
  externalId: StringFilter

  """Filter by the object’s `owner` field."""
  owner: StringFilter

  """Filter by the object’s `tokenClassesByClass` relation."""
  tokenClassesByClass: EntityToManyTokenClassFilter

  """Some related `tokenClassesByClass` exist."""
  tokenClassesByClassExist: Boolean

  """Filter by the object’s `tokensByCollection` relation."""
  tokensByCollection: EntityToManyTokenFilter

  """Some related `tokensByCollection` exist."""
  tokensByCollectionExist: Boolean

  """Filter by the object’s `iidById` relation."""
  iidById: IidFilter

  """Checks for all expressions in this list."""
  and: [EntityFilter!]

  """Checks for any expressions in this list."""
  or: [EntityFilter!]

  """Negates the expression."""
  not: EntityFilter
}

"""
A filter to be used against many `TokenClass` object types. All fields are combined with a logical ‘and.’
"""
input EntityToManyTokenClassFilter {
  """
  Every related `TokenClass` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: TokenClassFilter

  """
  Some related `TokenClass` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: TokenClassFilter

  """
  No related `TokenClass` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: TokenClassFilter
}

"""
A filter to be used against many `Token` object types. All fields are combined with a logical ‘and.’
"""
input EntityToManyTokenFilter {
  """
  Every related `Token` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: TokenFilter

  """
  Some related `Token` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: TokenFilter

  """
  No related `Token` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: TokenFilter
}

type Evaluation implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  collectionId: String!
  oracle: String!
  agentDid: String!
  agentAddress: String!
  status: Int!
  reason: Int!
  verificationProof: String
  amount: JSON!
  evaluationDate: Datetime!
  claimId: String!

  """Reads a single `Claim` that is related to this `Evaluation`."""
  claim: Claim
}

"""
A condition to be used against `Evaluation` object types. All fields are tested
for equality and combined with a logical ‘and.’
"""
input EvaluationCondition {
  """Checks for equality with the object’s `collectionId` field."""
  collectionId: String

  """Checks for equality with the object’s `oracle` field."""
  oracle: String

  """Checks for equality with the object’s `agentDid` field."""
  agentDid: String

  """Checks for equality with the object’s `agentAddress` field."""
  agentAddress: String

  """Checks for equality with the object’s `status` field."""
  status: Int

  """Checks for equality with the object’s `reason` field."""
  reason: Int

  """Checks for equality with the object’s `verificationProof` field."""
  verificationProof: String

  """Checks for equality with the object’s `amount` field."""
  amount: JSON

  """Checks for equality with the object’s `evaluationDate` field."""
  evaluationDate: Datetime

  """Checks for equality with the object’s `claimId` field."""
  claimId: String
}

"""
A filter to be used against `Evaluation` object types. All fields are combined with a logical ‘and.’
"""
input EvaluationFilter {
  """Filter by the object’s `collectionId` field."""
  collectionId: StringFilter

  """Filter by the object’s `oracle` field."""
  oracle: StringFilter

  """Filter by the object’s `agentDid` field."""
  agentDid: StringFilter

  """Filter by the object’s `agentAddress` field."""
  agentAddress: StringFilter

  """Filter by the object’s `status` field."""
  status: IntFilter

  """Filter by the object’s `reason` field."""
  reason: IntFilter

  """Filter by the object’s `verificationProof` field."""
  verificationProof: StringFilter

  """Filter by the object’s `amount` field."""
  amount: JSONFilter

  """Filter by the object’s `evaluationDate` field."""
  evaluationDate: DatetimeFilter

  """Filter by the object’s `claimId` field."""
  claimId: StringFilter

  """Filter by the object’s `claim` relation."""
  claim: ClaimFilter

  """Checks for all expressions in this list."""
  and: [EvaluationFilter!]

  """Checks for any expressions in this list."""
  or: [EvaluationFilter!]

  """Negates the expression."""
  not: EvaluationFilter
}

"""A connection to a list of `Evaluation` values."""
type EvaluationsConnection {
  """A list of `Evaluation` objects."""
  nodes: [Evaluation!]!

  """
  A list of edges which contains the `Evaluation` and cursor to aid in pagination.
  """
  edges: [EvaluationsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `Evaluation` you could get from the connection."""
  totalCount: Int!
}

"""A `Evaluation` edge in the connection."""
type EvaluationsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `Evaluation` at the end of the edge."""
  node: Evaluation!
}

"""Methods to use when ordering `Evaluation`."""
enum EvaluationsOrderBy {
  NATURAL
  COLLECTION_ID_ASC
  COLLECTION_ID_DESC
  ORACLE_ASC
  ORACLE_DESC
  AGENT_DID_ASC
  AGENT_DID_DESC
  AGENT_ADDRESS_ASC
  AGENT_ADDRESS_DESC
  STATUS_ASC
  STATUS_DESC
  REASON_ASC
  REASON_DESC
  VERIFICATION_PROOF_ASC
  VERIFICATION_PROOF_DESC
  AMOUNT_ASC
  AMOUNT_DESC
  EVALUATION_DATE_ASC
  EVALUATION_DATE_DESC
  CLAIM_ID_ASC
  CLAIM_ID_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

input HavingBigintFilter {
  equalTo: BigInt
  notEqualTo: BigInt
  greaterThan: BigInt
  greaterThanOrEqualTo: BigInt
  lessThan: BigInt
  lessThanOrEqualTo: BigInt
}

input HavingIntFilter {
  equalTo: Int
  notEqualTo: Int
  greaterThan: Int
  greaterThanOrEqualTo: Int
  lessThan: Int
  lessThanOrEqualTo: Int
}

type Iid implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  id: String!
  context: JSON!
  controller: [String]
  verificationMethod: JSON!
  service: JSON!
  authentication: [String]
  assertionMethod: [String]
  keyAgreement: [String]
  capabilityInvocation: [String]
  capabilityDelegation: [String]
  linkedResource: JSON!
  linkedClaim: JSON!
  accordedRight: JSON!
  linkedEntity: JSON!
  alsoKnownAs: String!
  metadata: JSON!

  """Reads a single `Entity` that is related to this `Iid`."""
  entityById: Entity
}

"""
A condition to be used against `Iid` object types. All fields are tested for equality and combined with a logical ‘and.’
"""
input IidCondition {
  """Checks for equality with the object’s `id` field."""
  id: String

  """Checks for equality with the object’s `context` field."""
  context: JSON

  """Checks for equality with the object’s `controller` field."""
  controller: [String]

  """Checks for equality with the object’s `verificationMethod` field."""
  verificationMethod: JSON

  """Checks for equality with the object’s `service` field."""
  service: JSON

  """Checks for equality with the object’s `authentication` field."""
  authentication: [String]

  """Checks for equality with the object’s `assertionMethod` field."""
  assertionMethod: [String]

  """Checks for equality with the object’s `keyAgreement` field."""
  keyAgreement: [String]

  """Checks for equality with the object’s `capabilityInvocation` field."""
  capabilityInvocation: [String]

  """Checks for equality with the object’s `capabilityDelegation` field."""
  capabilityDelegation: [String]

  """Checks for equality with the object’s `linkedResource` field."""
  linkedResource: JSON

  """Checks for equality with the object’s `linkedClaim` field."""
  linkedClaim: JSON

  """Checks for equality with the object’s `accordedRight` field."""
  accordedRight: JSON

  """Checks for equality with the object’s `linkedEntity` field."""
  linkedEntity: JSON

  """Checks for equality with the object’s `alsoKnownAs` field."""
  alsoKnownAs: String

  """Checks for equality with the object’s `metadata` field."""
  metadata: JSON
}

"""
A filter to be used against `Iid` object types. All fields are combined with a logical ‘and.’
"""
input IidFilter {
  """Filter by the object’s `id` field."""
  id: StringFilter

  """Filter by the object’s `context` field."""
  context: JSONFilter

  """Filter by the object’s `controller` field."""
  controller: StringListFilter

  """Filter by the object’s `verificationMethod` field."""
  verificationMethod: JSONFilter

  """Filter by the object’s `service` field."""
  service: JSONFilter

  """Filter by the object’s `authentication` field."""
  authentication: StringListFilter

  """Filter by the object’s `assertionMethod` field."""
  assertionMethod: StringListFilter

  """Filter by the object’s `keyAgreement` field."""
  keyAgreement: StringListFilter

  """Filter by the object’s `capabilityInvocation` field."""
  capabilityInvocation: StringListFilter

  """Filter by the object’s `capabilityDelegation` field."""
  capabilityDelegation: StringListFilter

  """Filter by the object’s `linkedResource` field."""
  linkedResource: JSONFilter

  """Filter by the object’s `linkedClaim` field."""
  linkedClaim: JSONFilter

  """Filter by the object’s `accordedRight` field."""
  accordedRight: JSONFilter

  """Filter by the object’s `linkedEntity` field."""
  linkedEntity: JSONFilter

  """Filter by the object’s `alsoKnownAs` field."""
  alsoKnownAs: StringFilter

  """Filter by the object’s `metadata` field."""
  metadata: JSONFilter

  """Filter by the object’s `entityById` relation."""
  entityById: EntityFilter

  """A related `entityById` exists."""
  entityByIdExists: Boolean

  """Checks for all expressions in this list."""
  and: [IidFilter!]

  """Checks for any expressions in this list."""
  or: [IidFilter!]

  """Negates the expression."""
  not: IidFilter
}

"""A connection to a list of `Iid` values."""
type IidsConnection {
  """A list of `Iid` objects."""
  nodes: [Iid!]!

  """
  A list of edges which contains the `Iid` and cursor to aid in pagination.
  """
  edges: [IidsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `Iid` you could get from the connection."""
  totalCount: Int!
}

"""A `Iid` edge in the connection."""
type IidsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `Iid` at the end of the edge."""
  node: Iid!
}

"""Methods to use when ordering `Iid`."""
enum IidsOrderBy {
  NATURAL
  ID_ASC
  ID_DESC
  CONTEXT_ASC
  CONTEXT_DESC
  CONTROLLER_ASC
  CONTROLLER_DESC
  VERIFICATION_METHOD_ASC
  VERIFICATION_METHOD_DESC
  SERVICE_ASC
  SERVICE_DESC
  AUTHENTICATION_ASC
  AUTHENTICATION_DESC
  ASSERTION_METHOD_ASC
  ASSERTION_METHOD_DESC
  KEY_AGREEMENT_ASC
  KEY_AGREEMENT_DESC
  CAPABILITY_INVOCATION_ASC
  CAPABILITY_INVOCATION_DESC
  CAPABILITY_DELEGATION_ASC
  CAPABILITY_DELEGATION_DESC
  LINKED_RESOURCE_ASC
  LINKED_RESOURCE_DESC
  LINKED_CLAIM_ASC
  LINKED_CLAIM_DESC
  ACCORDED_RIGHT_ASC
  ACCORDED_RIGHT_DESC
  LINKED_ENTITY_ASC
  LINKED_ENTITY_DESC
  ALSO_KNOWN_AS_ASC
  ALSO_KNOWN_AS_DESC
  METADATA_ASC
  METADATA_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

"""
A filter to be used against Int fields. All fields are combined with a logical ‘and.’
"""
input IntFilter {
  """
  Is null (if `true` is specified) or is not null (if `false` is specified).
  """
  isNull: Boolean

  """Equal to the specified value."""
  equalTo: Int

  """Not equal to the specified value."""
  notEqualTo: Int

  """
  Not equal to the specified value, treating null like an ordinary value.
  """
  distinctFrom: Int

  """Equal to the specified value, treating null like an ordinary value."""
  notDistinctFrom: Int

  """Included in the specified list."""
  in: [Int!]

  """Not included in the specified list."""
  notIn: [Int!]

  """Less than the specified value."""
  lessThan: Int

  """Less than or equal to the specified value."""
  lessThanOrEqualTo: Int

  """Greater than the specified value."""
  greaterThan: Int

  """Greater than or equal to the specified value."""
  greaterThanOrEqualTo: Int
}

type Ipf implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  cid: String!
  contentType: String!
  data: String!
}

"""
A condition to be used against `Ipf` object types. All fields are tested for equality and combined with a logical ‘and.’
"""
input IpfCondition {
  """Checks for equality with the object’s `cid` field."""
  cid: String

  """Checks for equality with the object’s `contentType` field."""
  contentType: String

  """Checks for equality with the object’s `data` field."""
  data: String
}

"""
A filter to be used against `Ipf` object types. All fields are combined with a logical ‘and.’
"""
input IpfFilter {
  """Filter by the object’s `cid` field."""
  cid: StringFilter

  """Filter by the object’s `contentType` field."""
  contentType: StringFilter

  """Filter by the object’s `data` field."""
  data: StringFilter

  """Checks for all expressions in this list."""
  and: [IpfFilter!]

  """Checks for any expressions in this list."""
  or: [IpfFilter!]

  """Negates the expression."""
  not: IpfFilter
}

"""A connection to a list of `Ipf` values."""
type IpfsConnection {
  """A list of `Ipf` objects."""
  nodes: [Ipf!]!

  """
  A list of edges which contains the `Ipf` and cursor to aid in pagination.
  """
  edges: [IpfsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `Ipf` you could get from the connection."""
  totalCount: Int!
}

"""A `Ipf` edge in the connection."""
type IpfsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `Ipf` at the end of the edge."""
  node: Ipf!
}

"""Methods to use when ordering `Ipf`."""
enum IpfsOrderBy {
  NATURAL
  CID_ASC
  CID_DESC
  CONTENT_TYPE_ASC
  CONTENT_TYPE_DESC
  DATA_ASC
  DATA_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

type IxoSwap implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  address: String!
  lpAddress: String!
  token1155Denom: String!
  token1155Reserve: BigInt!
  token2Denom: String!
  token2Reserve: BigInt!
  protocolFeeRecipient: String!
  protocolFeePercent: String!
  lpFeePercent: String!
  maxSlippagePercent: String!
  frozen: Boolean!
  owner: String!
  pendingOwner: String

  """Reads and enables pagination through a set of `IxoSwapPriceHistory`."""
  ixoSwapPriceHistoriesByAddress(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `IxoSwapPriceHistory`."""
    orderBy: [IxoSwapPriceHistoriesOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: IxoSwapPriceHistoryCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: IxoSwapPriceHistoryFilter
  ): IxoSwapPriceHistoriesConnection!
}

"""
A condition to be used against `IxoSwap` object types. All fields are tested for equality and combined with a logical ‘and.’
"""
input IxoSwapCondition {
  """Checks for equality with the object’s `address` field."""
  address: String

  """Checks for equality with the object’s `lpAddress` field."""
  lpAddress: String

  """Checks for equality with the object’s `token1155Denom` field."""
  token1155Denom: String

  """Checks for equality with the object’s `token1155Reserve` field."""
  token1155Reserve: BigInt

  """Checks for equality with the object’s `token2Denom` field."""
  token2Denom: String

  """Checks for equality with the object’s `token2Reserve` field."""
  token2Reserve: BigInt

  """Checks for equality with the object’s `protocolFeeRecipient` field."""
  protocolFeeRecipient: String

  """Checks for equality with the object’s `protocolFeePercent` field."""
  protocolFeePercent: String

  """Checks for equality with the object’s `lpFeePercent` field."""
  lpFeePercent: String

  """Checks for equality with the object’s `maxSlippagePercent` field."""
  maxSlippagePercent: String

  """Checks for equality with the object’s `frozen` field."""
  frozen: Boolean

  """Checks for equality with the object’s `owner` field."""
  owner: String

  """Checks for equality with the object’s `pendingOwner` field."""
  pendingOwner: String
}

"""
A filter to be used against `IxoSwap` object types. All fields are combined with a logical ‘and.’
"""
input IxoSwapFilter {
  """Filter by the object’s `address` field."""
  address: StringFilter

  """Filter by the object’s `lpAddress` field."""
  lpAddress: StringFilter

  """Filter by the object’s `token1155Denom` field."""
  token1155Denom: StringFilter

  """Filter by the object’s `token1155Reserve` field."""
  token1155Reserve: BigIntFilter

  """Filter by the object’s `token2Denom` field."""
  token2Denom: StringFilter

  """Filter by the object’s `token2Reserve` field."""
  token2Reserve: BigIntFilter

  """Filter by the object’s `protocolFeeRecipient` field."""
  protocolFeeRecipient: StringFilter

  """Filter by the object’s `protocolFeePercent` field."""
  protocolFeePercent: StringFilter

  """Filter by the object’s `lpFeePercent` field."""
  lpFeePercent: StringFilter

  """Filter by the object’s `maxSlippagePercent` field."""
  maxSlippagePercent: StringFilter

  """Filter by the object’s `frozen` field."""
  frozen: BooleanFilter

  """Filter by the object’s `owner` field."""
  owner: StringFilter

  """Filter by the object’s `pendingOwner` field."""
  pendingOwner: StringFilter

  """Filter by the object’s `ixoSwapPriceHistoriesByAddress` relation."""
  ixoSwapPriceHistoriesByAddress: IxoSwapToManyIxoSwapPriceHistoryFilter

  """Some related `ixoSwapPriceHistoriesByAddress` exist."""
  ixoSwapPriceHistoriesByAddressExist: Boolean

  """Checks for all expressions in this list."""
  and: [IxoSwapFilter!]

  """Checks for any expressions in this list."""
  or: [IxoSwapFilter!]

  """Negates the expression."""
  not: IxoSwapFilter
}

"""A connection to a list of `IxoSwapPriceHistory` values."""
type IxoSwapPriceHistoriesConnection {
  """A list of `IxoSwapPriceHistory` objects."""
  nodes: [IxoSwapPriceHistory!]!

  """
  A list of edges which contains the `IxoSwapPriceHistory` and cursor to aid in pagination.
  """
  edges: [IxoSwapPriceHistoriesEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """
  The count of *all* `IxoSwapPriceHistory` you could get from the connection.
  """
  totalCount: Int!
}

"""A `IxoSwapPriceHistory` edge in the connection."""
type IxoSwapPriceHistoriesEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `IxoSwapPriceHistory` at the end of the edge."""
  node: IxoSwapPriceHistory!
}

"""Methods to use when ordering `IxoSwapPriceHistory`."""
enum IxoSwapPriceHistoriesOrderBy {
  NATURAL
  ID_ASC
  ID_DESC
  ADDRESS_ASC
  ADDRESS_DESC
  TIMESTAMP_ASC
  TIMESTAMP_DESC
  TOKEN_1155_PRICE_ASC
  TOKEN_1155_PRICE_DESC
  TOKEN_2_PRICE_ASC
  TOKEN_2_PRICE_DESC
  TOKEN_1155_VOLUME_ASC
  TOKEN_1155_VOLUME_DESC
  TOKEN_2_VOLUME_ASC
  TOKEN_2_VOLUME_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

type IxoSwapPriceHistory implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  id: Int!
  address: String!
  timestamp: Datetime!
  token1155Price: BigFloat!
  token2Price: BigFloat!
  token1155Volume: BigFloat!
  token2Volume: BigFloat!

  """
  Reads a single `IxoSwap` that is related to this `IxoSwapPriceHistory`.
  """
  ixoSwapByAddress: IxoSwap
}

"""
A condition to be used against `IxoSwapPriceHistory` object types. All fields
are tested for equality and combined with a logical ‘and.’
"""
input IxoSwapPriceHistoryCondition {
  """Checks for equality with the object’s `id` field."""
  id: Int

  """Checks for equality with the object’s `address` field."""
  address: String

  """Checks for equality with the object’s `timestamp` field."""
  timestamp: Datetime

  """Checks for equality with the object’s `token1155Price` field."""
  token1155Price: BigFloat

  """Checks for equality with the object’s `token2Price` field."""
  token2Price: BigFloat

  """Checks for equality with the object’s `token1155Volume` field."""
  token1155Volume: BigFloat

  """Checks for equality with the object’s `token2Volume` field."""
  token2Volume: BigFloat
}

"""
A filter to be used against `IxoSwapPriceHistory` object types. All fields are combined with a logical ‘and.’
"""
input IxoSwapPriceHistoryFilter {
  """Filter by the object’s `id` field."""
  id: IntFilter

  """Filter by the object’s `address` field."""
  address: StringFilter

  """Filter by the object’s `timestamp` field."""
  timestamp: DatetimeFilter

  """Filter by the object’s `token1155Price` field."""
  token1155Price: BigFloatFilter

  """Filter by the object’s `token2Price` field."""
  token2Price: BigFloatFilter

  """Filter by the object’s `token1155Volume` field."""
  token1155Volume: BigFloatFilter

  """Filter by the object’s `token2Volume` field."""
  token2Volume: BigFloatFilter

  """Filter by the object’s `ixoSwapByAddress` relation."""
  ixoSwapByAddress: IxoSwapFilter

  """Checks for all expressions in this list."""
  and: [IxoSwapPriceHistoryFilter!]

  """Checks for any expressions in this list."""
  or: [IxoSwapPriceHistoryFilter!]

  """Negates the expression."""
  not: IxoSwapPriceHistoryFilter
}

"""A connection to a list of `IxoSwap` values."""
type IxoSwapsConnection {
  """A list of `IxoSwap` objects."""
  nodes: [IxoSwap!]!

  """
  A list of edges which contains the `IxoSwap` and cursor to aid in pagination.
  """
  edges: [IxoSwapsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `IxoSwap` you could get from the connection."""
  totalCount: Int!
}

"""A `IxoSwap` edge in the connection."""
type IxoSwapsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `IxoSwap` at the end of the edge."""
  node: IxoSwap!
}

"""Methods to use when ordering `IxoSwap`."""
enum IxoSwapsOrderBy {
  NATURAL
  ADDRESS_ASC
  ADDRESS_DESC
  LP_ADDRESS_ASC
  LP_ADDRESS_DESC
  TOKEN_1155_DENOM_ASC
  TOKEN_1155_DENOM_DESC
  TOKEN_1155_RESERVE_ASC
  TOKEN_1155_RESERVE_DESC
  TOKEN_2_DENOM_ASC
  TOKEN_2_DENOM_DESC
  TOKEN_2_RESERVE_ASC
  TOKEN_2_RESERVE_DESC
  PROTOCOL_FEE_RECIPIENT_ASC
  PROTOCOL_FEE_RECIPIENT_DESC
  PROTOCOL_FEE_PERCENT_ASC
  PROTOCOL_FEE_PERCENT_DESC
  LP_FEE_PERCENT_ASC
  LP_FEE_PERCENT_DESC
  MAX_SLIPPAGE_PERCENT_ASC
  MAX_SLIPPAGE_PERCENT_DESC
  FROZEN_ASC
  FROZEN_DESC
  OWNER_ASC
  OWNER_DESC
  PENDING_OWNER_ASC
  PENDING_OWNER_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

"""
A filter to be used against many `IxoSwapPriceHistory` object types. All fields are combined with a logical ‘and.’
"""
input IxoSwapToManyIxoSwapPriceHistoryFilter {
  """
  Every related `IxoSwapPriceHistory` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: IxoSwapPriceHistoryFilter

  """
  Some related `IxoSwapPriceHistory` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: IxoSwapPriceHistoryFilter

  """
  No related `IxoSwapPriceHistory` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: IxoSwapPriceHistoryFilter
}

"""
The `JSON` scalar type represents JSON values as specified by [ECMA-404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf).
"""
scalar JSON

"""
A filter to be used against JSON fields. All fields are combined with a logical ‘and.’
"""
input JSONFilter {
  """
  Is null (if `true` is specified) or is not null (if `false` is specified).
  """
  isNull: Boolean

  """Equal to the specified value."""
  equalTo: JSON

  """Not equal to the specified value."""
  notEqualTo: JSON

  """
  Not equal to the specified value, treating null like an ordinary value.
  """
  distinctFrom: JSON

  """Equal to the specified value, treating null like an ordinary value."""
  notDistinctFrom: JSON

  """Included in the specified list."""
  in: [JSON!]

  """Not included in the specified list."""
  notIn: [JSON!]

  """Less than the specified value."""
  lessThan: JSON

  """Less than or equal to the specified value."""
  lessThanOrEqualTo: JSON

  """Greater than the specified value."""
  greaterThan: JSON

  """Greater than or equal to the specified value."""
  greaterThanOrEqualTo: JSON

  """Contains the specified JSON."""
  contains: JSON

  """Contains the specified key."""
  containsKey: String

  """Contains all of the specified keys."""
  containsAllKeys: [String!]

  """Contains any of the specified keys."""
  containsAnyKeys: [String!]

  """Contained by the specified JSON."""
  containedBy: JSON
}

type Message implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  id: Int!
  typeUrl: String!
  value: JSON!
  from: String
  to: String
  denoms: [String]
  tokenNames: [String]
  transactionHash: String!

  """Reads a single `Transaction` that is related to this `Message`."""
  transactionByTransactionHash: Transaction
}

"""
A condition to be used against `Message` object types. All fields are tested for equality and combined with a logical ‘and.’
"""
input MessageCondition {
  """Checks for equality with the object’s `id` field."""
  id: Int

  """Checks for equality with the object’s `typeUrl` field."""
  typeUrl: String

  """Checks for equality with the object’s `value` field."""
  value: JSON

  """Checks for equality with the object’s `from` field."""
  from: String

  """Checks for equality with the object’s `to` field."""
  to: String

  """Checks for equality with the object’s `denoms` field."""
  denoms: [String]

  """Checks for equality with the object’s `tokenNames` field."""
  tokenNames: [String]

  """Checks for equality with the object’s `transactionHash` field."""
  transactionHash: String
}

"""
A filter to be used against `Message` object types. All fields are combined with a logical ‘and.’
"""
input MessageFilter {
  """Filter by the object’s `id` field."""
  id: IntFilter

  """Filter by the object’s `typeUrl` field."""
  typeUrl: StringFilter

  """Filter by the object’s `value` field."""
  value: JSONFilter

  """Filter by the object’s `from` field."""
  from: StringFilter

  """Filter by the object’s `to` field."""
  to: StringFilter

  """Filter by the object’s `denoms` field."""
  denoms: StringListFilter

  """Filter by the object’s `tokenNames` field."""
  tokenNames: StringListFilter

  """Filter by the object’s `transactionHash` field."""
  transactionHash: StringFilter

  """Filter by the object’s `transactionByTransactionHash` relation."""
  transactionByTransactionHash: TransactionFilter

  """Checks for all expressions in this list."""
  and: [MessageFilter!]

  """Checks for any expressions in this list."""
  or: [MessageFilter!]

  """Negates the expression."""
  not: MessageFilter
}

"""A connection to a list of `Message` values."""
type MessagesConnection {
  """A list of `Message` objects."""
  nodes: [Message!]!

  """
  A list of edges which contains the `Message` and cursor to aid in pagination.
  """
  edges: [MessagesEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `Message` you could get from the connection."""
  totalCount: Int!
}

"""A `Message` edge in the connection."""
type MessagesEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `Message` at the end of the edge."""
  node: Message!
}

"""Methods to use when ordering `Message`."""
enum MessagesOrderBy {
  NATURAL
  ID_ASC
  ID_DESC
  TYPE_URL_ASC
  TYPE_URL_DESC
  VALUE_ASC
  VALUE_DESC
  FROM_ASC
  FROM_DESC
  TO_ASC
  TO_DESC
  DENOMS_ASC
  DENOMS_DESC
  TOKEN_NAMES_ASC
  TOKEN_NAMES_DESC
  TRANSACTION_HASH_ASC
  TRANSACTION_HASH_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

"""An object with a globally unique `ID`."""
interface Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
}

type OutcomePayment implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  id: Int!
  bondDid: String!
  senderDid: String!
  senderAddress: String!
  amount: JSON!
  height: Int!
  timestamp: Datetime!

  """Reads a single `Bond` that is related to this `OutcomePayment`."""
  bondByBondDid: Bond
}

"""
A condition to be used against `OutcomePayment` object types. All fields are
tested for equality and combined with a logical ‘and.’
"""
input OutcomePaymentCondition {
  """Checks for equality with the object’s `id` field."""
  id: Int

  """Checks for equality with the object’s `bondDid` field."""
  bondDid: String

  """Checks for equality with the object’s `senderDid` field."""
  senderDid: String

  """Checks for equality with the object’s `senderAddress` field."""
  senderAddress: String

  """Checks for equality with the object’s `amount` field."""
  amount: JSON

  """Checks for equality with the object’s `height` field."""
  height: Int

  """Checks for equality with the object’s `timestamp` field."""
  timestamp: Datetime
}

"""
A filter to be used against `OutcomePayment` object types. All fields are combined with a logical ‘and.’
"""
input OutcomePaymentFilter {
  """Filter by the object’s `id` field."""
  id: IntFilter

  """Filter by the object’s `bondDid` field."""
  bondDid: StringFilter

  """Filter by the object’s `senderDid` field."""
  senderDid: StringFilter

  """Filter by the object’s `senderAddress` field."""
  senderAddress: StringFilter

  """Filter by the object’s `amount` field."""
  amount: JSONFilter

  """Filter by the object’s `height` field."""
  height: IntFilter

  """Filter by the object’s `timestamp` field."""
  timestamp: DatetimeFilter

  """Filter by the object’s `bondByBondDid` relation."""
  bondByBondDid: BondFilter

  """Checks for all expressions in this list."""
  and: [OutcomePaymentFilter!]

  """Checks for any expressions in this list."""
  or: [OutcomePaymentFilter!]

  """Negates the expression."""
  not: OutcomePaymentFilter
}

"""A connection to a list of `OutcomePayment` values."""
type OutcomePaymentsConnection {
  """A list of `OutcomePayment` objects."""
  nodes: [OutcomePayment!]!

  """
  A list of edges which contains the `OutcomePayment` and cursor to aid in pagination.
  """
  edges: [OutcomePaymentsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `OutcomePayment` you could get from the connection."""
  totalCount: Int!
}

"""A `OutcomePayment` edge in the connection."""
type OutcomePaymentsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `OutcomePayment` at the end of the edge."""
  node: OutcomePayment!
}

"""Methods to use when ordering `OutcomePayment`."""
enum OutcomePaymentsOrderBy {
  NATURAL
  ID_ASC
  ID_DESC
  BOND_DID_ASC
  BOND_DID_DESC
  SENDER_DID_ASC
  SENDER_DID_DESC
  SENDER_ADDRESS_ASC
  SENDER_ADDRESS_DESC
  AMOUNT_ASC
  AMOUNT_DESC
  HEIGHT_ASC
  HEIGHT_DESC
  TIMESTAMP_ASC
  TIMESTAMP_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

"""Information about pagination in a connection."""
type PageInfo {
  """When paginating forwards, are there more items?"""
  hasNextPage: Boolean!

  """When paginating backwards, are there more items?"""
  hasPreviousPage: Boolean!

  """When paginating backwards, the cursor to continue."""
  startCursor: Cursor

  """When paginating forwards, the cursor to continue."""
  endCursor: Cursor
}

type Pgmigration implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  id: Int!
  name: String!
  runOn: Datetime!
}

"""
A condition to be used against `Pgmigration` object types. All fields are tested
for equality and combined with a logical ‘and.’
"""
input PgmigrationCondition {
  """Checks for equality with the object’s `id` field."""
  id: Int

  """Checks for equality with the object’s `name` field."""
  name: String

  """Checks for equality with the object’s `runOn` field."""
  runOn: Datetime
}

"""
A filter to be used against `Pgmigration` object types. All fields are combined with a logical ‘and.’
"""
input PgmigrationFilter {
  """Filter by the object’s `id` field."""
  id: IntFilter

  """Filter by the object’s `name` field."""
  name: StringFilter

  """Filter by the object’s `runOn` field."""
  runOn: DatetimeFilter

  """Checks for all expressions in this list."""
  and: [PgmigrationFilter!]

  """Checks for any expressions in this list."""
  or: [PgmigrationFilter!]

  """Negates the expression."""
  not: PgmigrationFilter
}

"""A connection to a list of `Pgmigration` values."""
type PgmigrationsConnection {
  """A list of `Pgmigration` objects."""
  nodes: [Pgmigration!]!

  """
  A list of edges which contains the `Pgmigration` and cursor to aid in pagination.
  """
  edges: [PgmigrationsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `Pgmigration` you could get from the connection."""
  totalCount: Int!
}

"""A `Pgmigration` edge in the connection."""
type PgmigrationsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `Pgmigration` at the end of the edge."""
  node: Pgmigration!
}

"""Methods to use when ordering `Pgmigration`."""
enum PgmigrationsOrderBy {
  NATURAL
  ID_ASC
  ID_DESC
  NAME_ASC
  NAME_DESC
  RUN_ON_ASC
  RUN_ON_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

"""The root query type which gives access points into the data universe."""
type Query implements Node {
  """
  Exposes the root query type nested one level down. This is helpful for Relay 1
  which can only query top level fields if they are in a particular form.
  """
  query: Query!

  """
  The root query type must be a `Node` to work well with Relay 1 mutations. This just resolves to `query`.
  """
  nodeId: ID!

  """Fetches an object given its globally unique `ID`."""
  node(
    """The globally unique `ID`."""
    nodeId: ID!
  ): Node

  """Reads and enables pagination through a set of `Bond`."""
  bonds(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Bond`."""
    orderBy: [BondsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: BondCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: BondFilter
  ): BondsConnection

  """Reads and enables pagination through a set of `BondAlpha`."""
  bondAlphas(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `BondAlpha`."""
    orderBy: [BondAlphasOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: BondAlphaCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: BondAlphaFilter
  ): BondAlphasConnection

  """Reads and enables pagination through a set of `BondBuy`."""
  bondBuys(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `BondBuy`."""
    orderBy: [BondBuysOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: BondBuyCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: BondBuyFilter
  ): BondBuysConnection

  """Reads and enables pagination through a set of `BondSell`."""
  bondSells(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `BondSell`."""
    orderBy: [BondSellsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: BondSellCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: BondSellFilter
  ): BondSellsConnection

  """Reads and enables pagination through a set of `BondSwap`."""
  bondSwaps(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `BondSwap`."""
    orderBy: [BondSwapsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: BondSwapCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: BondSwapFilter
  ): BondSwapsConnection

  """Reads and enables pagination through a set of `Chain`."""
  chains(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Chain`."""
    orderBy: [ChainsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: ChainCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: ChainFilter
  ): ChainsConnection

  """Reads and enables pagination through a set of `Claim`."""
  claims(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Claim`."""
    orderBy: [ClaimsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: ClaimCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: ClaimFilter
  ): ClaimsConnection

  """Reads and enables pagination through a set of `ClaimCollection`."""
  claimCollections(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `ClaimCollection`."""
    orderBy: [ClaimCollectionsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: ClaimCollectionCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: ClaimCollectionFilter
  ): ClaimCollectionsConnection

  """Reads and enables pagination through a set of `Dispute`."""
  disputes(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Dispute`."""
    orderBy: [DisputesOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: DisputeCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: DisputeFilter
  ): DisputesConnection

  """Reads and enables pagination through a set of `Entity`."""
  entities(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Entity`."""
    orderBy: [EntitiesOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: EntityCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: EntityFilter
  ): EntitiesConnection

  """Reads and enables pagination through a set of `Evaluation`."""
  evaluations(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Evaluation`."""
    orderBy: [EvaluationsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: EvaluationCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: EvaluationFilter
  ): EvaluationsConnection

  """Reads and enables pagination through a set of `Iid`."""
  iids(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Iid`."""
    orderBy: [IidsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: IidCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: IidFilter
  ): IidsConnection

  """Reads and enables pagination through a set of `Ipf`."""
  ipfs(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Ipf`."""
    orderBy: [IpfsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: IpfCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: IpfFilter
  ): IpfsConnection

  """Reads and enables pagination through a set of `Message`."""
  messages(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Message`."""
    orderBy: [MessagesOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: MessageCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: MessageFilter
  ): MessagesConnection

  """Reads and enables pagination through a set of `OutcomePayment`."""
  outcomePayments(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `OutcomePayment`."""
    orderBy: [OutcomePaymentsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: OutcomePaymentCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: OutcomePaymentFilter
  ): OutcomePaymentsConnection

  """Reads and enables pagination through a set of `ReserveWithdrawal`."""
  reserveWithdrawals(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `ReserveWithdrawal`."""
    orderBy: [ReserveWithdrawalsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: ReserveWithdrawalCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: ReserveWithdrawalFilter
  ): ReserveWithdrawalsConnection

  """Reads and enables pagination through a set of `ShareWithdrawal`."""
  shareWithdrawals(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `ShareWithdrawal`."""
    orderBy: [ShareWithdrawalsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: ShareWithdrawalCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: ShareWithdrawalFilter
  ): ShareWithdrawalsConnection

  """Reads and enables pagination through a set of `Token`."""
  tokens(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Token`."""
    orderBy: [TokensOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TokenCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TokenFilter
  ): TokensConnection

  """Reads and enables pagination through a set of `TokenCancelled`."""
  tokenCancelleds(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `TokenCancelled`."""
    orderBy: [TokenCancelledsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TokenCancelledCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TokenCancelledFilter
  ): TokenCancelledsConnection

  """Reads and enables pagination through a set of `TokenClass`."""
  tokenClasses(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `TokenClass`."""
    orderBy: [TokenClassesOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TokenClassCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TokenClassFilter
  ): TokenClassesConnection

  """Reads and enables pagination through a set of `TokenDatum`."""
  tokenData(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `TokenDatum`."""
    orderBy: [TokenDataOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TokenDatumCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TokenDatumFilter
  ): TokenDataConnection

  """Reads and enables pagination through a set of `TokenRetired`."""
  tokenRetireds(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `TokenRetired`."""
    orderBy: [TokenRetiredsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TokenRetiredCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TokenRetiredFilter
  ): TokenRetiredsConnection

  """Reads and enables pagination through a set of `TokenTransaction`."""
  tokenTransactions(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `TokenTransaction`."""
    orderBy: [TokenTransactionsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TokenTransactionCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TokenTransactionFilter
  ): TokenTransactionsConnection

  """Reads and enables pagination through a set of `TokenomicsAccount`."""
  tokenomicsAccounts(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `TokenomicsAccount`."""
    orderBy: [TokenomicsAccountsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TokenomicsAccountCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TokenomicsAccountFilter
  ): TokenomicsAccountsConnection

  """Reads and enables pagination through a set of `Transaction`."""
  transactions(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Transaction`."""
    orderBy: [TransactionsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TransactionCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TransactionFilter
  ): TransactionsConnection

  """Reads and enables pagination through a set of `IxoSwap`."""
  ixoSwaps(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `IxoSwap`."""
    orderBy: [IxoSwapsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: IxoSwapCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: IxoSwapFilter
  ): IxoSwapsConnection

  """Reads and enables pagination through a set of `IxoSwapPriceHistory`."""
  ixoSwapPriceHistories(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `IxoSwapPriceHistory`."""
    orderBy: [IxoSwapPriceHistoriesOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: IxoSwapPriceHistoryCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: IxoSwapPriceHistoryFilter
  ): IxoSwapPriceHistoriesConnection

  """Reads and enables pagination through a set of `Pgmigration`."""
  pgmigrations(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Pgmigration`."""
    orderBy: [PgmigrationsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: PgmigrationCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: PgmigrationFilter
  ): PgmigrationsConnection
  bond(bondDid: String!): Bond
  bondAlpha(id: Int!): BondAlpha
  bondBuy(id: Int!): BondBuy
  bondSell(id: Int!): BondSell
  bondSwap(id: Int!): BondSwap
  chain(chainId: String!): Chain
  claim(claimId: String!): Claim
  claimCollection(id: String!): ClaimCollection
  dispute(proof: String!): Dispute
  entity(id: String!): Entity
  evaluation(claimId: String!): Evaluation
  iid(id: String!): Iid
  ipf(cid: String!): Ipf
  message(id: Int!): Message
  outcomePayment(id: Int!): OutcomePayment
  reserveWithdrawal(id: Int!): ReserveWithdrawal
  shareWithdrawal(id: Int!): ShareWithdrawal
  token(id: String!): Token
  tokenCancelled(aid: Int!): TokenCancelled
  tokenClass(contractAddress: String!): TokenClass
  tokenDatum(aid: Int!): TokenDatum
  tokenRetired(aid: Int!): TokenRetired
  tokenTransaction(aid: Int!): TokenTransaction
  tokenomicsAccount(address: String!): TokenomicsAccount
  transaction(hash: String!): Transaction
  ixoSwap(address: String!): IxoSwap
  ixoSwapPriceHistory(id: Int!): IxoSwapPriceHistory
  ixoSwapPriceHistoryByTimestampAndAddress(timestamp: Datetime!, address: String!): IxoSwapPriceHistory
  pgmigration(id: Int!): Pgmigration

  """Reads a single `Bond` using its globally unique `ID`."""
  bondByNodeId(
    """The globally unique `ID` to be used in selecting a single `Bond`."""
    nodeId: ID!
  ): Bond

  """Reads a single `BondAlpha` using its globally unique `ID`."""
  bondAlphaByNodeId(
    """The globally unique `ID` to be used in selecting a single `BondAlpha`."""
    nodeId: ID!
  ): BondAlpha

  """Reads a single `BondBuy` using its globally unique `ID`."""
  bondBuyByNodeId(
    """The globally unique `ID` to be used in selecting a single `BondBuy`."""
    nodeId: ID!
  ): BondBuy

  """Reads a single `BondSell` using its globally unique `ID`."""
  bondSellByNodeId(
    """The globally unique `ID` to be used in selecting a single `BondSell`."""
    nodeId: ID!
  ): BondSell

  """Reads a single `BondSwap` using its globally unique `ID`."""
  bondSwapByNodeId(
    """The globally unique `ID` to be used in selecting a single `BondSwap`."""
    nodeId: ID!
  ): BondSwap

  """Reads a single `Chain` using its globally unique `ID`."""
  chainByNodeId(
    """The globally unique `ID` to be used in selecting a single `Chain`."""
    nodeId: ID!
  ): Chain

  """Reads a single `Claim` using its globally unique `ID`."""
  claimByNodeId(
    """The globally unique `ID` to be used in selecting a single `Claim`."""
    nodeId: ID!
  ): Claim

  """Reads a single `ClaimCollection` using its globally unique `ID`."""
  claimCollectionByNodeId(
    """
    The globally unique `ID` to be used in selecting a single `ClaimCollection`.
    """
    nodeId: ID!
  ): ClaimCollection

  """Reads a single `Dispute` using its globally unique `ID`."""
  disputeByNodeId(
    """The globally unique `ID` to be used in selecting a single `Dispute`."""
    nodeId: ID!
  ): Dispute

  """Reads a single `Entity` using its globally unique `ID`."""
  entityByNodeId(
    """The globally unique `ID` to be used in selecting a single `Entity`."""
    nodeId: ID!
  ): Entity

  """Reads a single `Evaluation` using its globally unique `ID`."""
  evaluationByNodeId(
    """
    The globally unique `ID` to be used in selecting a single `Evaluation`.
    """
    nodeId: ID!
  ): Evaluation

  """Reads a single `Iid` using its globally unique `ID`."""
  iidByNodeId(
    """The globally unique `ID` to be used in selecting a single `Iid`."""
    nodeId: ID!
  ): Iid

  """Reads a single `Ipf` using its globally unique `ID`."""
  ipfByNodeId(
    """The globally unique `ID` to be used in selecting a single `Ipf`."""
    nodeId: ID!
  ): Ipf

  """Reads a single `Message` using its globally unique `ID`."""
  messageByNodeId(
    """The globally unique `ID` to be used in selecting a single `Message`."""
    nodeId: ID!
  ): Message

  """Reads a single `OutcomePayment` using its globally unique `ID`."""
  outcomePaymentByNodeId(
    """
    The globally unique `ID` to be used in selecting a single `OutcomePayment`.
    """
    nodeId: ID!
  ): OutcomePayment

  """Reads a single `ReserveWithdrawal` using its globally unique `ID`."""
  reserveWithdrawalByNodeId(
    """
    The globally unique `ID` to be used in selecting a single `ReserveWithdrawal`.
    """
    nodeId: ID!
  ): ReserveWithdrawal

  """Reads a single `ShareWithdrawal` using its globally unique `ID`."""
  shareWithdrawalByNodeId(
    """
    The globally unique `ID` to be used in selecting a single `ShareWithdrawal`.
    """
    nodeId: ID!
  ): ShareWithdrawal

  """Reads a single `Token` using its globally unique `ID`."""
  tokenByNodeId(
    """The globally unique `ID` to be used in selecting a single `Token`."""
    nodeId: ID!
  ): Token

  """Reads a single `TokenCancelled` using its globally unique `ID`."""
  tokenCancelledByNodeId(
    """
    The globally unique `ID` to be used in selecting a single `TokenCancelled`.
    """
    nodeId: ID!
  ): TokenCancelled

  """Reads a single `TokenClass` using its globally unique `ID`."""
  tokenClassByNodeId(
    """
    The globally unique `ID` to be used in selecting a single `TokenClass`.
    """
    nodeId: ID!
  ): TokenClass

  """Reads a single `TokenDatum` using its globally unique `ID`."""
  tokenDatumByNodeId(
    """
    The globally unique `ID` to be used in selecting a single `TokenDatum`.
    """
    nodeId: ID!
  ): TokenDatum

  """Reads a single `TokenRetired` using its globally unique `ID`."""
  tokenRetiredByNodeId(
    """
    The globally unique `ID` to be used in selecting a single `TokenRetired`.
    """
    nodeId: ID!
  ): TokenRetired

  """Reads a single `TokenTransaction` using its globally unique `ID`."""
  tokenTransactionByNodeId(
    """
    The globally unique `ID` to be used in selecting a single `TokenTransaction`.
    """
    nodeId: ID!
  ): TokenTransaction

  """Reads a single `TokenomicsAccount` using its globally unique `ID`."""
  tokenomicsAccountByNodeId(
    """
    The globally unique `ID` to be used in selecting a single `TokenomicsAccount`.
    """
    nodeId: ID!
  ): TokenomicsAccount

  """Reads a single `Transaction` using its globally unique `ID`."""
  transactionByNodeId(
    """
    The globally unique `ID` to be used in selecting a single `Transaction`.
    """
    nodeId: ID!
  ): Transaction

  """Reads a single `IxoSwap` using its globally unique `ID`."""
  ixoSwapByNodeId(
    """The globally unique `ID` to be used in selecting a single `IxoSwap`."""
    nodeId: ID!
  ): IxoSwap

  """Reads a single `IxoSwapPriceHistory` using its globally unique `ID`."""
  ixoSwapPriceHistoryByNodeId(
    """
    The globally unique `ID` to be used in selecting a single `IxoSwapPriceHistory`.
    """
    nodeId: ID!
  ): IxoSwapPriceHistory

  """Reads a single `Pgmigration` using its globally unique `ID`."""
  pgmigrationByNodeId(
    """
    The globally unique `ID` to be used in selecting a single `Pgmigration`.
    """
    nodeId: ID!
  ): Pgmigration
  getAccountTokens(address: String!, name: String, allEntityRetired: Boolean): JSON!
  getTokensTotalByAddress(address: String!, name: String, allEntityRetired: Boolean): JSON!
  getTokensTotalForEntities(address: String!, name: String, allEntityRetired: Boolean): JSON!
  getTokensTotalForCollection(did: String!, name: String, allEntityRetired: Boolean): JSON!
  getTokensTotalForCollectionAmounts(did: String!, name: String, allEntityRetired: Boolean): JSON!
  deviceExternalIdsLoaded: Boolean!
  tokenomicsSupplyTotal: JSON!
  tokenomicsSupplyCommunityPool: JSON!
  tokenomicsInflation: JSON!
  tokenomicsSupplyStaked: JSON!
  tokenomicsSupplyIBC: JSON!
}

type ReserveWithdrawal implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  id: Int!
  bondDid: String!
  withdrawerDid: String!
  withdrawerAddress: String!
  amount: JSON!
  reserveWithdrawalAddress: String!
  height: Int!
  timestamp: Datetime!

  """Reads a single `Bond` that is related to this `ReserveWithdrawal`."""
  bondByBondDid: Bond
}

"""
A condition to be used against `ReserveWithdrawal` object types. All fields are
tested for equality and combined with a logical ‘and.’
"""
input ReserveWithdrawalCondition {
  """Checks for equality with the object’s `id` field."""
  id: Int

  """Checks for equality with the object’s `bondDid` field."""
  bondDid: String

  """Checks for equality with the object’s `withdrawerDid` field."""
  withdrawerDid: String

  """Checks for equality with the object’s `withdrawerAddress` field."""
  withdrawerAddress: String

  """Checks for equality with the object’s `amount` field."""
  amount: JSON

  """
  Checks for equality with the object’s `reserveWithdrawalAddress` field.
  """
  reserveWithdrawalAddress: String

  """Checks for equality with the object’s `height` field."""
  height: Int

  """Checks for equality with the object’s `timestamp` field."""
  timestamp: Datetime
}

"""
A filter to be used against `ReserveWithdrawal` object types. All fields are combined with a logical ‘and.’
"""
input ReserveWithdrawalFilter {
  """Filter by the object’s `id` field."""
  id: IntFilter

  """Filter by the object’s `bondDid` field."""
  bondDid: StringFilter

  """Filter by the object’s `withdrawerDid` field."""
  withdrawerDid: StringFilter

  """Filter by the object’s `withdrawerAddress` field."""
  withdrawerAddress: StringFilter

  """Filter by the object’s `amount` field."""
  amount: JSONFilter

  """Filter by the object’s `reserveWithdrawalAddress` field."""
  reserveWithdrawalAddress: StringFilter

  """Filter by the object’s `height` field."""
  height: IntFilter

  """Filter by the object’s `timestamp` field."""
  timestamp: DatetimeFilter

  """Filter by the object’s `bondByBondDid` relation."""
  bondByBondDid: BondFilter

  """Checks for all expressions in this list."""
  and: [ReserveWithdrawalFilter!]

  """Checks for any expressions in this list."""
  or: [ReserveWithdrawalFilter!]

  """Negates the expression."""
  not: ReserveWithdrawalFilter
}

"""A connection to a list of `ReserveWithdrawal` values."""
type ReserveWithdrawalsConnection {
  """A list of `ReserveWithdrawal` objects."""
  nodes: [ReserveWithdrawal!]!

  """
  A list of edges which contains the `ReserveWithdrawal` and cursor to aid in pagination.
  """
  edges: [ReserveWithdrawalsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """
  The count of *all* `ReserveWithdrawal` you could get from the connection.
  """
  totalCount: Int!
}

"""A `ReserveWithdrawal` edge in the connection."""
type ReserveWithdrawalsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `ReserveWithdrawal` at the end of the edge."""
  node: ReserveWithdrawal!
}

"""Methods to use when ordering `ReserveWithdrawal`."""
enum ReserveWithdrawalsOrderBy {
  NATURAL
  ID_ASC
  ID_DESC
  BOND_DID_ASC
  BOND_DID_DESC
  WITHDRAWER_DID_ASC
  WITHDRAWER_DID_DESC
  WITHDRAWER_ADDRESS_ASC
  WITHDRAWER_ADDRESS_DESC
  AMOUNT_ASC
  AMOUNT_DESC
  RESERVE_WITHDRAWAL_ADDRESS_ASC
  RESERVE_WITHDRAWAL_ADDRESS_DESC
  HEIGHT_ASC
  HEIGHT_DESC
  TIMESTAMP_ASC
  TIMESTAMP_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

type ShareWithdrawal implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  id: Int!
  bondDid: String!
  recipientDid: String!
  recipientAddress: String!
  amount: JSON!
  height: Int!
  timestamp: Datetime!

  """Reads a single `Bond` that is related to this `ShareWithdrawal`."""
  bondByBondDid: Bond
}

"""
A condition to be used against `ShareWithdrawal` object types. All fields are
tested for equality and combined with a logical ‘and.’
"""
input ShareWithdrawalCondition {
  """Checks for equality with the object’s `id` field."""
  id: Int

  """Checks for equality with the object’s `bondDid` field."""
  bondDid: String

  """Checks for equality with the object’s `recipientDid` field."""
  recipientDid: String

  """Checks for equality with the object’s `recipientAddress` field."""
  recipientAddress: String

  """Checks for equality with the object’s `amount` field."""
  amount: JSON

  """Checks for equality with the object’s `height` field."""
  height: Int

  """Checks for equality with the object’s `timestamp` field."""
  timestamp: Datetime
}

"""
A filter to be used against `ShareWithdrawal` object types. All fields are combined with a logical ‘and.’
"""
input ShareWithdrawalFilter {
  """Filter by the object’s `id` field."""
  id: IntFilter

  """Filter by the object’s `bondDid` field."""
  bondDid: StringFilter

  """Filter by the object’s `recipientDid` field."""
  recipientDid: StringFilter

  """Filter by the object’s `recipientAddress` field."""
  recipientAddress: StringFilter

  """Filter by the object’s `amount` field."""
  amount: JSONFilter

  """Filter by the object’s `height` field."""
  height: IntFilter

  """Filter by the object’s `timestamp` field."""
  timestamp: DatetimeFilter

  """Filter by the object’s `bondByBondDid` relation."""
  bondByBondDid: BondFilter

  """Checks for all expressions in this list."""
  and: [ShareWithdrawalFilter!]

  """Checks for any expressions in this list."""
  or: [ShareWithdrawalFilter!]

  """Negates the expression."""
  not: ShareWithdrawalFilter
}

"""A connection to a list of `ShareWithdrawal` values."""
type ShareWithdrawalsConnection {
  """A list of `ShareWithdrawal` objects."""
  nodes: [ShareWithdrawal!]!

  """
  A list of edges which contains the `ShareWithdrawal` and cursor to aid in pagination.
  """
  edges: [ShareWithdrawalsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """
  The count of *all* `ShareWithdrawal` you could get from the connection.
  """
  totalCount: Int!
}

"""A `ShareWithdrawal` edge in the connection."""
type ShareWithdrawalsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `ShareWithdrawal` at the end of the edge."""
  node: ShareWithdrawal!
}

"""Methods to use when ordering `ShareWithdrawal`."""
enum ShareWithdrawalsOrderBy {
  NATURAL
  ID_ASC
  ID_DESC
  BOND_DID_ASC
  BOND_DID_DESC
  RECIPIENT_DID_ASC
  RECIPIENT_DID_DESC
  RECIPIENT_ADDRESS_ASC
  RECIPIENT_ADDRESS_DESC
  AMOUNT_ASC
  AMOUNT_DESC
  HEIGHT_ASC
  HEIGHT_DESC
  TIMESTAMP_ASC
  TIMESTAMP_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

"""
A filter to be used against String fields. All fields are combined with a logical ‘and.’
"""
input StringFilter {
  """
  Is null (if `true` is specified) or is not null (if `false` is specified).
  """
  isNull: Boolean

  """Equal to the specified value."""
  equalTo: String

  """Not equal to the specified value."""
  notEqualTo: String

  """
  Not equal to the specified value, treating null like an ordinary value.
  """
  distinctFrom: String

  """Equal to the specified value, treating null like an ordinary value."""
  notDistinctFrom: String

  """Included in the specified list."""
  in: [String!]

  """Not included in the specified list."""
  notIn: [String!]

  """Less than the specified value."""
  lessThan: String

  """Less than or equal to the specified value."""
  lessThanOrEqualTo: String

  """Greater than the specified value."""
  greaterThan: String

  """Greater than or equal to the specified value."""
  greaterThanOrEqualTo: String

  """Contains the specified string (case-sensitive)."""
  includes: String

  """Does not contain the specified string (case-sensitive)."""
  notIncludes: String

  """Contains the specified string (case-insensitive)."""
  includesInsensitive: String

  """Does not contain the specified string (case-insensitive)."""
  notIncludesInsensitive: String

  """Starts with the specified string (case-sensitive)."""
  startsWith: String

  """Does not start with the specified string (case-sensitive)."""
  notStartsWith: String

  """Starts with the specified string (case-insensitive)."""
  startsWithInsensitive: String

  """Does not start with the specified string (case-insensitive)."""
  notStartsWithInsensitive: String

  """Ends with the specified string (case-sensitive)."""
  endsWith: String

  """Does not end with the specified string (case-sensitive)."""
  notEndsWith: String

  """Ends with the specified string (case-insensitive)."""
  endsWithInsensitive: String

  """Does not end with the specified string (case-insensitive)."""
  notEndsWithInsensitive: String

  """
  Matches the specified pattern (case-sensitive). An underscore (_) matches any
  single character; a percent sign (%) matches any sequence of zero or more characters.
  """
  like: String

  """
  Does not match the specified pattern (case-sensitive). An underscore (_)
  matches any single character; a percent sign (%) matches any sequence of zero
  or more characters.
  """
  notLike: String

  """
  Matches the specified pattern (case-insensitive). An underscore (_) matches
  any single character; a percent sign (%) matches any sequence of zero or more characters.
  """
  likeInsensitive: String

  """
  Does not match the specified pattern (case-insensitive). An underscore (_)
  matches any single character; a percent sign (%) matches any sequence of zero
  or more characters.
  """
  notLikeInsensitive: String

  """Equal to the specified value (case-insensitive)."""
  equalToInsensitive: String

  """Not equal to the specified value (case-insensitive)."""
  notEqualToInsensitive: String

  """
  Not equal to the specified value, treating null like an ordinary value (case-insensitive).
  """
  distinctFromInsensitive: String

  """
  Equal to the specified value, treating null like an ordinary value (case-insensitive).
  """
  notDistinctFromInsensitive: String

  """Included in the specified list (case-insensitive)."""
  inInsensitive: [String!]

  """Not included in the specified list (case-insensitive)."""
  notInInsensitive: [String!]

  """Less than the specified value (case-insensitive)."""
  lessThanInsensitive: String

  """Less than or equal to the specified value (case-insensitive)."""
  lessThanOrEqualToInsensitive: String

  """Greater than the specified value (case-insensitive)."""
  greaterThanInsensitive: String

  """Greater than or equal to the specified value (case-insensitive)."""
  greaterThanOrEqualToInsensitive: String
}

"""
A filter to be used against String List fields. All fields are combined with a logical ‘and.’
"""
input StringListFilter {
  """
  Is null (if `true` is specified) or is not null (if `false` is specified).
  """
  isNull: Boolean

  """Equal to the specified value."""
  equalTo: [String]

  """Not equal to the specified value."""
  notEqualTo: [String]

  """
  Not equal to the specified value, treating null like an ordinary value.
  """
  distinctFrom: [String]

  """Equal to the specified value, treating null like an ordinary value."""
  notDistinctFrom: [String]

  """Less than the specified value."""
  lessThan: [String]

  """Less than or equal to the specified value."""
  lessThanOrEqualTo: [String]

  """Greater than the specified value."""
  greaterThan: [String]

  """Greater than or equal to the specified value."""
  greaterThanOrEqualTo: [String]

  """Contains the specified list of values."""
  contains: [String]

  """Contained by the specified list of values."""
  containedBy: [String]

  """Overlaps the specified list of values."""
  overlaps: [String]

  """Any array item is equal to the specified value."""
  anyEqualTo: String

  """Any array item is not equal to the specified value."""
  anyNotEqualTo: String

  """Any array item is less than the specified value."""
  anyLessThan: String

  """Any array item is less than or equal to the specified value."""
  anyLessThanOrEqualTo: String

  """Any array item is greater than the specified value."""
  anyGreaterThan: String

  """Any array item is greater than or equal to the specified value."""
  anyGreaterThanOrEqualTo: String
}

type Token implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  id: String!
  index: String!
  name: String!
  collection: String!

  """Reads a single `TokenClass` that is related to this `Token`."""
  tokenClassByName: TokenClass

  """Reads a single `Entity` that is related to this `Token`."""
  entityByCollection: Entity

  """Reads and enables pagination through a set of `TokenDatum`."""
  tokenDataByTokenId(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `TokenDatum`."""
    orderBy: [TokenDataOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TokenDatumCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TokenDatumFilter
  ): TokenDataConnection!

  """Reads and enables pagination through a set of `TokenRetired`."""
  tokenRetiredsById(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `TokenRetired`."""
    orderBy: [TokenRetiredsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TokenRetiredCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TokenRetiredFilter
  ): TokenRetiredsConnection!

  """Reads and enables pagination through a set of `TokenTransaction`."""
  tokenTransactionsByTokenId(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `TokenTransaction`."""
    orderBy: [TokenTransactionsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TokenTransactionCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TokenTransactionFilter
  ): TokenTransactionsConnection!
}

type TokenCancelled implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  aid: Int!
  id: String!
  reason: String!
  amount: BigInt!
  owner: String!
  name: String!

  """Reads a single `TokenClass` that is related to this `TokenCancelled`."""
  tokenClassByName: TokenClass
}

type TokenCancelledAggregates {
  keys: [String!]

  """
  Sum aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  sum: TokenCancelledSumAggregates

  """
  Distinct count aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  distinctCount: TokenCancelledDistinctCountAggregates

  """
  Minimum aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  min: TokenCancelledMinAggregates

  """
  Maximum aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  max: TokenCancelledMaxAggregates

  """
  Mean average aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  average: TokenCancelledAverageAggregates

  """
  Sample standard deviation aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  stddevSample: TokenCancelledStddevSampleAggregates

  """
  Population standard deviation aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  stddevPopulation: TokenCancelledStddevPopulationAggregates

  """
  Sample variance aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  varianceSample: TokenCancelledVarianceSampleAggregates

  """
  Population variance aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  variancePopulation: TokenCancelledVariancePopulationAggregates
}

"""
A filter to be used against aggregates of `TokenCancelled` object types.
"""
input TokenCancelledAggregatesFilter {
  """
  A filter that must pass for the relevant `TokenCancelled` object to be included within the aggregate.
  """
  filter: TokenCancelledFilter

  """Sum aggregate over matching `TokenCancelled` objects."""
  sum: TokenCancelledSumAggregateFilter

  """Distinct count aggregate over matching `TokenCancelled` objects."""
  distinctCount: TokenCancelledDistinctCountAggregateFilter

  """Minimum aggregate over matching `TokenCancelled` objects."""
  min: TokenCancelledMinAggregateFilter

  """Maximum aggregate over matching `TokenCancelled` objects."""
  max: TokenCancelledMaxAggregateFilter

  """Mean average aggregate over matching `TokenCancelled` objects."""
  average: TokenCancelledAverageAggregateFilter

  """
  Sample standard deviation aggregate over matching `TokenCancelled` objects.
  """
  stddevSample: TokenCancelledStddevSampleAggregateFilter

  """
  Population standard deviation aggregate over matching `TokenCancelled` objects.
  """
  stddevPopulation: TokenCancelledStddevPopulationAggregateFilter

  """Sample variance aggregate over matching `TokenCancelled` objects."""
  varianceSample: TokenCancelledVarianceSampleAggregateFilter

  """Population variance aggregate over matching `TokenCancelled` objects."""
  variancePopulation: TokenCancelledVariancePopulationAggregateFilter
}

input TokenCancelledAverageAggregateFilter {
  aid: BigFloatFilter
  amount: BigFloatFilter
}

type TokenCancelledAverageAggregates {
  """Mean average of aid across the matching connection"""
  aid: BigFloat

  """Mean average of amount across the matching connection"""
  amount: BigFloat
}

"""
A condition to be used against `TokenCancelled` object types. All fields are
tested for equality and combined with a logical ‘and.’
"""
input TokenCancelledCondition {
  """Checks for equality with the object’s `aid` field."""
  aid: Int

  """Checks for equality with the object’s `id` field."""
  id: String

  """Checks for equality with the object’s `reason` field."""
  reason: String

  """Checks for equality with the object’s `amount` field."""
  amount: BigInt

  """Checks for equality with the object’s `owner` field."""
  owner: String

  """Checks for equality with the object’s `name` field."""
  name: String
}

input TokenCancelledDistinctCountAggregateFilter {
  aid: BigIntFilter
  id: BigIntFilter
  reason: BigIntFilter
  amount: BigIntFilter
  owner: BigIntFilter
  name: BigIntFilter
}

type TokenCancelledDistinctCountAggregates {
  """Distinct count of aid across the matching connection"""
  aid: BigInt

  """Distinct count of id across the matching connection"""
  id: BigInt

  """Distinct count of reason across the matching connection"""
  reason: BigInt

  """Distinct count of amount across the matching connection"""
  amount: BigInt

  """Distinct count of owner across the matching connection"""
  owner: BigInt

  """Distinct count of name across the matching connection"""
  name: BigInt
}

"""
A filter to be used against `TokenCancelled` object types. All fields are combined with a logical ‘and.’
"""
input TokenCancelledFilter {
  """Filter by the object’s `aid` field."""
  aid: IntFilter

  """Filter by the object’s `id` field."""
  id: StringFilter

  """Filter by the object’s `reason` field."""
  reason: StringFilter

  """Filter by the object’s `amount` field."""
  amount: BigIntFilter

  """Filter by the object’s `owner` field."""
  owner: StringFilter

  """Filter by the object’s `name` field."""
  name: StringFilter

  """Filter by the object’s `tokenClassByName` relation."""
  tokenClassByName: TokenClassFilter

  """Checks for all expressions in this list."""
  and: [TokenCancelledFilter!]

  """Checks for any expressions in this list."""
  or: [TokenCancelledFilter!]

  """Negates the expression."""
  not: TokenCancelledFilter
}

"""Grouping methods for `TokenCancelled` for usage during aggregation."""
enum TokenCancelledGroupBy {
  ID
  REASON
  AMOUNT
  OWNER
  NAME
}

input TokenCancelledHavingAverageInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenCancelledHavingDistinctCountInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

"""Conditions for `TokenCancelled` aggregates."""
input TokenCancelledHavingInput {
  AND: [TokenCancelledHavingInput!]
  OR: [TokenCancelledHavingInput!]
  sum: TokenCancelledHavingSumInput
  distinctCount: TokenCancelledHavingDistinctCountInput
  min: TokenCancelledHavingMinInput
  max: TokenCancelledHavingMaxInput
  average: TokenCancelledHavingAverageInput
  stddevSample: TokenCancelledHavingStddevSampleInput
  stddevPopulation: TokenCancelledHavingStddevPopulationInput
  varianceSample: TokenCancelledHavingVarianceSampleInput
  variancePopulation: TokenCancelledHavingVariancePopulationInput
}

input TokenCancelledHavingMaxInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenCancelledHavingMinInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenCancelledHavingStddevPopulationInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenCancelledHavingStddevSampleInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenCancelledHavingSumInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenCancelledHavingVariancePopulationInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenCancelledHavingVarianceSampleInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenCancelledMaxAggregateFilter {
  aid: IntFilter
  amount: BigIntFilter
}

type TokenCancelledMaxAggregates {
  """Maximum of aid across the matching connection"""
  aid: Int

  """Maximum of amount across the matching connection"""
  amount: BigInt
}

input TokenCancelledMinAggregateFilter {
  aid: IntFilter
  amount: BigIntFilter
}

type TokenCancelledMinAggregates {
  """Minimum of aid across the matching connection"""
  aid: Int

  """Minimum of amount across the matching connection"""
  amount: BigInt
}

"""A connection to a list of `TokenCancelled` values."""
type TokenCancelledsConnection {
  """A list of `TokenCancelled` objects."""
  nodes: [TokenCancelled!]!

  """
  A list of edges which contains the `TokenCancelled` and cursor to aid in pagination.
  """
  edges: [TokenCancelledsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `TokenCancelled` you could get from the connection."""
  totalCount: Int!

  """
  Aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  aggregates: TokenCancelledAggregates

  """
  Grouped aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  groupedAggregates(
    """The method to use when grouping `TokenCancelled` for these aggregates."""
    groupBy: [TokenCancelledGroupBy!]!

    """Conditions on the grouped aggregates."""
    having: TokenCancelledHavingInput
  ): [TokenCancelledAggregates!]
}

"""A `TokenCancelled` edge in the connection."""
type TokenCancelledsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `TokenCancelled` at the end of the edge."""
  node: TokenCancelled!
}

"""Methods to use when ordering `TokenCancelled`."""
enum TokenCancelledsOrderBy {
  NATURAL
  AID_ASC
  AID_DESC
  ID_ASC
  ID_DESC
  REASON_ASC
  REASON_DESC
  AMOUNT_ASC
  AMOUNT_DESC
  OWNER_ASC
  OWNER_DESC
  NAME_ASC
  NAME_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

input TokenCancelledStddevPopulationAggregateFilter {
  aid: BigFloatFilter
  amount: BigFloatFilter
}

type TokenCancelledStddevPopulationAggregates {
  """Population standard deviation of aid across the matching connection"""
  aid: BigFloat

  """Population standard deviation of amount across the matching connection"""
  amount: BigFloat
}

input TokenCancelledStddevSampleAggregateFilter {
  aid: BigFloatFilter
  amount: BigFloatFilter
}

type TokenCancelledStddevSampleAggregates {
  """Sample standard deviation of aid across the matching connection"""
  aid: BigFloat

  """Sample standard deviation of amount across the matching connection"""
  amount: BigFloat
}

input TokenCancelledSumAggregateFilter {
  aid: BigIntFilter
  amount: BigFloatFilter
}

type TokenCancelledSumAggregates {
  """Sum of aid across the matching connection"""
  aid: BigInt!

  """Sum of amount across the matching connection"""
  amount: BigFloat!
}

input TokenCancelledVariancePopulationAggregateFilter {
  aid: BigFloatFilter
  amount: BigFloatFilter
}

type TokenCancelledVariancePopulationAggregates {
  """Population variance of aid across the matching connection"""
  aid: BigFloat

  """Population variance of amount across the matching connection"""
  amount: BigFloat
}

input TokenCancelledVarianceSampleAggregateFilter {
  aid: BigFloatFilter
  amount: BigFloatFilter
}

type TokenCancelledVarianceSampleAggregates {
  """Sample variance of aid across the matching connection"""
  aid: BigFloat

  """Sample variance of amount across the matching connection"""
  amount: BigFloat
}

type TokenClass implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  contractAddress: String!
  minter: String!
  class: String!
  name: String!
  description: String!
  image: String!
  type: String!
  cap: BigInt!
  supply: BigInt!
  paused: Boolean!
  stopped: Boolean!

  """Reads a single `Entity` that is related to this `TokenClass`."""
  entityByClass: Entity

  """Reads and enables pagination through a set of `Token`."""
  tokensByName(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Token`."""
    orderBy: [TokensOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TokenCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TokenFilter
  ): TokensConnection!

  """Reads and enables pagination through a set of `TokenRetired`."""
  tokenRetiredsByName(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `TokenRetired`."""
    orderBy: [TokenRetiredsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TokenRetiredCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TokenRetiredFilter
  ): TokenRetiredsConnection!

  """Reads and enables pagination through a set of `TokenCancelled`."""
  tokenCancelledsByName(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `TokenCancelled`."""
    orderBy: [TokenCancelledsOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: TokenCancelledCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: TokenCancelledFilter
  ): TokenCancelledsConnection!
}

"""
A condition to be used against `TokenClass` object types. All fields are tested
for equality and combined with a logical ‘and.’
"""
input TokenClassCondition {
  """Checks for equality with the object’s `contractAddress` field."""
  contractAddress: String

  """Checks for equality with the object’s `minter` field."""
  minter: String

  """Checks for equality with the object’s `class` field."""
  class: String

  """Checks for equality with the object’s `name` field."""
  name: String

  """Checks for equality with the object’s `description` field."""
  description: String

  """Checks for equality with the object’s `image` field."""
  image: String

  """Checks for equality with the object’s `type` field."""
  type: String

  """Checks for equality with the object’s `cap` field."""
  cap: BigInt

  """Checks for equality with the object’s `supply` field."""
  supply: BigInt

  """Checks for equality with the object’s `paused` field."""
  paused: Boolean

  """Checks for equality with the object’s `stopped` field."""
  stopped: Boolean
}

"""A connection to a list of `TokenClass` values."""
type TokenClassesConnection {
  """A list of `TokenClass` objects."""
  nodes: [TokenClass!]!

  """
  A list of edges which contains the `TokenClass` and cursor to aid in pagination.
  """
  edges: [TokenClassesEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `TokenClass` you could get from the connection."""
  totalCount: Int!
}

"""A `TokenClass` edge in the connection."""
type TokenClassesEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `TokenClass` at the end of the edge."""
  node: TokenClass!
}

"""Methods to use when ordering `TokenClass`."""
enum TokenClassesOrderBy {
  NATURAL
  CONTRACT_ADDRESS_ASC
  CONTRACT_ADDRESS_DESC
  MINTER_ASC
  MINTER_DESC
  CLASS_ASC
  CLASS_DESC
  NAME_ASC
  NAME_DESC
  DESCRIPTION_ASC
  DESCRIPTION_DESC
  IMAGE_ASC
  IMAGE_DESC
  TYPE_ASC
  TYPE_DESC
  CAP_ASC
  CAP_DESC
  SUPPLY_ASC
  SUPPLY_DESC
  PAUSED_ASC
  PAUSED_DESC
  STOPPED_ASC
  STOPPED_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
  TOKEN_RETIREDS_BY_NAME_COUNT_ASC
  TOKEN_RETIREDS_BY_NAME_COUNT_DESC
  TOKEN_RETIREDS_BY_NAME_SUM_AID_ASC
  TOKEN_RETIREDS_BY_NAME_SUM_AID_DESC
  TOKEN_RETIREDS_BY_NAME_SUM_ID_ASC
  TOKEN_RETIREDS_BY_NAME_SUM_ID_DESC
  TOKEN_RETIREDS_BY_NAME_SUM_REASON_ASC
  TOKEN_RETIREDS_BY_NAME_SUM_REASON_DESC
  TOKEN_RETIREDS_BY_NAME_SUM_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_NAME_SUM_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_NAME_SUM_AMOUNT_ASC
  TOKEN_RETIREDS_BY_NAME_SUM_AMOUNT_DESC
  TOKEN_RETIREDS_BY_NAME_SUM_OWNER_ASC
  TOKEN_RETIREDS_BY_NAME_SUM_OWNER_DESC
  TOKEN_RETIREDS_BY_NAME_SUM_NAME_ASC
  TOKEN_RETIREDS_BY_NAME_SUM_NAME_DESC
  TOKEN_RETIREDS_BY_NAME_DISTINCT_COUNT_AID_ASC
  TOKEN_RETIREDS_BY_NAME_DISTINCT_COUNT_AID_DESC
  TOKEN_RETIREDS_BY_NAME_DISTINCT_COUNT_ID_ASC
  TOKEN_RETIREDS_BY_NAME_DISTINCT_COUNT_ID_DESC
  TOKEN_RETIREDS_BY_NAME_DISTINCT_COUNT_REASON_ASC
  TOKEN_RETIREDS_BY_NAME_DISTINCT_COUNT_REASON_DESC
  TOKEN_RETIREDS_BY_NAME_DISTINCT_COUNT_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_NAME_DISTINCT_COUNT_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_NAME_DISTINCT_COUNT_AMOUNT_ASC
  TOKEN_RETIREDS_BY_NAME_DISTINCT_COUNT_AMOUNT_DESC
  TOKEN_RETIREDS_BY_NAME_DISTINCT_COUNT_OWNER_ASC
  TOKEN_RETIREDS_BY_NAME_DISTINCT_COUNT_OWNER_DESC
  TOKEN_RETIREDS_BY_NAME_DISTINCT_COUNT_NAME_ASC
  TOKEN_RETIREDS_BY_NAME_DISTINCT_COUNT_NAME_DESC
  TOKEN_RETIREDS_BY_NAME_MIN_AID_ASC
  TOKEN_RETIREDS_BY_NAME_MIN_AID_DESC
  TOKEN_RETIREDS_BY_NAME_MIN_ID_ASC
  TOKEN_RETIREDS_BY_NAME_MIN_ID_DESC
  TOKEN_RETIREDS_BY_NAME_MIN_REASON_ASC
  TOKEN_RETIREDS_BY_NAME_MIN_REASON_DESC
  TOKEN_RETIREDS_BY_NAME_MIN_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_NAME_MIN_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_NAME_MIN_AMOUNT_ASC
  TOKEN_RETIREDS_BY_NAME_MIN_AMOUNT_DESC
  TOKEN_RETIREDS_BY_NAME_MIN_OWNER_ASC
  TOKEN_RETIREDS_BY_NAME_MIN_OWNER_DESC
  TOKEN_RETIREDS_BY_NAME_MIN_NAME_ASC
  TOKEN_RETIREDS_BY_NAME_MIN_NAME_DESC
  TOKEN_RETIREDS_BY_NAME_MAX_AID_ASC
  TOKEN_RETIREDS_BY_NAME_MAX_AID_DESC
  TOKEN_RETIREDS_BY_NAME_MAX_ID_ASC
  TOKEN_RETIREDS_BY_NAME_MAX_ID_DESC
  TOKEN_RETIREDS_BY_NAME_MAX_REASON_ASC
  TOKEN_RETIREDS_BY_NAME_MAX_REASON_DESC
  TOKEN_RETIREDS_BY_NAME_MAX_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_NAME_MAX_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_NAME_MAX_AMOUNT_ASC
  TOKEN_RETIREDS_BY_NAME_MAX_AMOUNT_DESC
  TOKEN_RETIREDS_BY_NAME_MAX_OWNER_ASC
  TOKEN_RETIREDS_BY_NAME_MAX_OWNER_DESC
  TOKEN_RETIREDS_BY_NAME_MAX_NAME_ASC
  TOKEN_RETIREDS_BY_NAME_MAX_NAME_DESC
  TOKEN_RETIREDS_BY_NAME_AVERAGE_AID_ASC
  TOKEN_RETIREDS_BY_NAME_AVERAGE_AID_DESC
  TOKEN_RETIREDS_BY_NAME_AVERAGE_ID_ASC
  TOKEN_RETIREDS_BY_NAME_AVERAGE_ID_DESC
  TOKEN_RETIREDS_BY_NAME_AVERAGE_REASON_ASC
  TOKEN_RETIREDS_BY_NAME_AVERAGE_REASON_DESC
  TOKEN_RETIREDS_BY_NAME_AVERAGE_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_NAME_AVERAGE_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_NAME_AVERAGE_AMOUNT_ASC
  TOKEN_RETIREDS_BY_NAME_AVERAGE_AMOUNT_DESC
  TOKEN_RETIREDS_BY_NAME_AVERAGE_OWNER_ASC
  TOKEN_RETIREDS_BY_NAME_AVERAGE_OWNER_DESC
  TOKEN_RETIREDS_BY_NAME_AVERAGE_NAME_ASC
  TOKEN_RETIREDS_BY_NAME_AVERAGE_NAME_DESC
  TOKEN_RETIREDS_BY_NAME_STDDEV_SAMPLE_AID_ASC
  TOKEN_RETIREDS_BY_NAME_STDDEV_SAMPLE_AID_DESC
  TOKEN_RETIREDS_BY_NAME_STDDEV_SAMPLE_ID_ASC
  TOKEN_RETIREDS_BY_NAME_STDDEV_SAMPLE_ID_DESC
  TOKEN_RETIREDS_BY_NAME_STDDEV_SAMPLE_REASON_ASC
  TOKEN_RETIREDS_BY_NAME_STDDEV_SAMPLE_REASON_DESC
  TOKEN_RETIREDS_BY_NAME_STDDEV_SAMPLE_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_NAME_STDDEV_SAMPLE_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_NAME_STDDEV_SAMPLE_AMOUNT_ASC
  TOKEN_RETIREDS_BY_NAME_STDDEV_SAMPLE_AMOUNT_DESC
  TOKEN_RETIREDS_BY_NAME_STDDEV_SAMPLE_OWNER_ASC
  TOKEN_RETIREDS_BY_NAME_STDDEV_SAMPLE_OWNER_DESC
  TOKEN_RETIREDS_BY_NAME_STDDEV_SAMPLE_NAME_ASC
  TOKEN_RETIREDS_BY_NAME_STDDEV_SAMPLE_NAME_DESC
  TOKEN_RETIREDS_BY_NAME_STDDEV_POPULATION_AID_ASC
  TOKEN_RETIREDS_BY_NAME_STDDEV_POPULATION_AID_DESC
  TOKEN_RETIREDS_BY_NAME_STDDEV_POPULATION_ID_ASC
  TOKEN_RETIREDS_BY_NAME_STDDEV_POPULATION_ID_DESC
  TOKEN_RETIREDS_BY_NAME_STDDEV_POPULATION_REASON_ASC
  TOKEN_RETIREDS_BY_NAME_STDDEV_POPULATION_REASON_DESC
  TOKEN_RETIREDS_BY_NAME_STDDEV_POPULATION_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_NAME_STDDEV_POPULATION_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_NAME_STDDEV_POPULATION_AMOUNT_ASC
  TOKEN_RETIREDS_BY_NAME_STDDEV_POPULATION_AMOUNT_DESC
  TOKEN_RETIREDS_BY_NAME_STDDEV_POPULATION_OWNER_ASC
  TOKEN_RETIREDS_BY_NAME_STDDEV_POPULATION_OWNER_DESC
  TOKEN_RETIREDS_BY_NAME_STDDEV_POPULATION_NAME_ASC
  TOKEN_RETIREDS_BY_NAME_STDDEV_POPULATION_NAME_DESC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_SAMPLE_AID_ASC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_SAMPLE_AID_DESC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_SAMPLE_ID_ASC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_SAMPLE_ID_DESC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_SAMPLE_REASON_ASC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_SAMPLE_REASON_DESC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_SAMPLE_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_SAMPLE_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_SAMPLE_AMOUNT_ASC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_SAMPLE_AMOUNT_DESC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_SAMPLE_OWNER_ASC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_SAMPLE_OWNER_DESC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_SAMPLE_NAME_ASC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_SAMPLE_NAME_DESC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_POPULATION_AID_ASC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_POPULATION_AID_DESC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_POPULATION_ID_ASC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_POPULATION_ID_DESC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_POPULATION_REASON_ASC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_POPULATION_REASON_DESC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_POPULATION_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_POPULATION_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_POPULATION_AMOUNT_ASC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_POPULATION_AMOUNT_DESC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_POPULATION_OWNER_ASC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_POPULATION_OWNER_DESC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_POPULATION_NAME_ASC
  TOKEN_RETIREDS_BY_NAME_VARIANCE_POPULATION_NAME_DESC
  TOKEN_CANCELLEDS_BY_NAME_COUNT_ASC
  TOKEN_CANCELLEDS_BY_NAME_COUNT_DESC
  TOKEN_CANCELLEDS_BY_NAME_SUM_AID_ASC
  TOKEN_CANCELLEDS_BY_NAME_SUM_AID_DESC
  TOKEN_CANCELLEDS_BY_NAME_SUM_ID_ASC
  TOKEN_CANCELLEDS_BY_NAME_SUM_ID_DESC
  TOKEN_CANCELLEDS_BY_NAME_SUM_REASON_ASC
  TOKEN_CANCELLEDS_BY_NAME_SUM_REASON_DESC
  TOKEN_CANCELLEDS_BY_NAME_SUM_AMOUNT_ASC
  TOKEN_CANCELLEDS_BY_NAME_SUM_AMOUNT_DESC
  TOKEN_CANCELLEDS_BY_NAME_SUM_OWNER_ASC
  TOKEN_CANCELLEDS_BY_NAME_SUM_OWNER_DESC
  TOKEN_CANCELLEDS_BY_NAME_SUM_NAME_ASC
  TOKEN_CANCELLEDS_BY_NAME_SUM_NAME_DESC
  TOKEN_CANCELLEDS_BY_NAME_DISTINCT_COUNT_AID_ASC
  TOKEN_CANCELLEDS_BY_NAME_DISTINCT_COUNT_AID_DESC
  TOKEN_CANCELLEDS_BY_NAME_DISTINCT_COUNT_ID_ASC
  TOKEN_CANCELLEDS_BY_NAME_DISTINCT_COUNT_ID_DESC
  TOKEN_CANCELLEDS_BY_NAME_DISTINCT_COUNT_REASON_ASC
  TOKEN_CANCELLEDS_BY_NAME_DISTINCT_COUNT_REASON_DESC
  TOKEN_CANCELLEDS_BY_NAME_DISTINCT_COUNT_AMOUNT_ASC
  TOKEN_CANCELLEDS_BY_NAME_DISTINCT_COUNT_AMOUNT_DESC
  TOKEN_CANCELLEDS_BY_NAME_DISTINCT_COUNT_OWNER_ASC
  TOKEN_CANCELLEDS_BY_NAME_DISTINCT_COUNT_OWNER_DESC
  TOKEN_CANCELLEDS_BY_NAME_DISTINCT_COUNT_NAME_ASC
  TOKEN_CANCELLEDS_BY_NAME_DISTINCT_COUNT_NAME_DESC
  TOKEN_CANCELLEDS_BY_NAME_MIN_AID_ASC
  TOKEN_CANCELLEDS_BY_NAME_MIN_AID_DESC
  TOKEN_CANCELLEDS_BY_NAME_MIN_ID_ASC
  TOKEN_CANCELLEDS_BY_NAME_MIN_ID_DESC
  TOKEN_CANCELLEDS_BY_NAME_MIN_REASON_ASC
  TOKEN_CANCELLEDS_BY_NAME_MIN_REASON_DESC
  TOKEN_CANCELLEDS_BY_NAME_MIN_AMOUNT_ASC
  TOKEN_CANCELLEDS_BY_NAME_MIN_AMOUNT_DESC
  TOKEN_CANCELLEDS_BY_NAME_MIN_OWNER_ASC
  TOKEN_CANCELLEDS_BY_NAME_MIN_OWNER_DESC
  TOKEN_CANCELLEDS_BY_NAME_MIN_NAME_ASC
  TOKEN_CANCELLEDS_BY_NAME_MIN_NAME_DESC
  TOKEN_CANCELLEDS_BY_NAME_MAX_AID_ASC
  TOKEN_CANCELLEDS_BY_NAME_MAX_AID_DESC
  TOKEN_CANCELLEDS_BY_NAME_MAX_ID_ASC
  TOKEN_CANCELLEDS_BY_NAME_MAX_ID_DESC
  TOKEN_CANCELLEDS_BY_NAME_MAX_REASON_ASC
  TOKEN_CANCELLEDS_BY_NAME_MAX_REASON_DESC
  TOKEN_CANCELLEDS_BY_NAME_MAX_AMOUNT_ASC
  TOKEN_CANCELLEDS_BY_NAME_MAX_AMOUNT_DESC
  TOKEN_CANCELLEDS_BY_NAME_MAX_OWNER_ASC
  TOKEN_CANCELLEDS_BY_NAME_MAX_OWNER_DESC
  TOKEN_CANCELLEDS_BY_NAME_MAX_NAME_ASC
  TOKEN_CANCELLEDS_BY_NAME_MAX_NAME_DESC
  TOKEN_CANCELLEDS_BY_NAME_AVERAGE_AID_ASC
  TOKEN_CANCELLEDS_BY_NAME_AVERAGE_AID_DESC
  TOKEN_CANCELLEDS_BY_NAME_AVERAGE_ID_ASC
  TOKEN_CANCELLEDS_BY_NAME_AVERAGE_ID_DESC
  TOKEN_CANCELLEDS_BY_NAME_AVERAGE_REASON_ASC
  TOKEN_CANCELLEDS_BY_NAME_AVERAGE_REASON_DESC
  TOKEN_CANCELLEDS_BY_NAME_AVERAGE_AMOUNT_ASC
  TOKEN_CANCELLEDS_BY_NAME_AVERAGE_AMOUNT_DESC
  TOKEN_CANCELLEDS_BY_NAME_AVERAGE_OWNER_ASC
  TOKEN_CANCELLEDS_BY_NAME_AVERAGE_OWNER_DESC
  TOKEN_CANCELLEDS_BY_NAME_AVERAGE_NAME_ASC
  TOKEN_CANCELLEDS_BY_NAME_AVERAGE_NAME_DESC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_SAMPLE_AID_ASC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_SAMPLE_AID_DESC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_SAMPLE_ID_ASC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_SAMPLE_ID_DESC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_SAMPLE_REASON_ASC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_SAMPLE_REASON_DESC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_SAMPLE_AMOUNT_ASC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_SAMPLE_AMOUNT_DESC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_SAMPLE_OWNER_ASC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_SAMPLE_OWNER_DESC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_SAMPLE_NAME_ASC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_SAMPLE_NAME_DESC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_POPULATION_AID_ASC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_POPULATION_AID_DESC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_POPULATION_ID_ASC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_POPULATION_ID_DESC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_POPULATION_REASON_ASC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_POPULATION_REASON_DESC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_POPULATION_AMOUNT_ASC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_POPULATION_AMOUNT_DESC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_POPULATION_OWNER_ASC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_POPULATION_OWNER_DESC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_POPULATION_NAME_ASC
  TOKEN_CANCELLEDS_BY_NAME_STDDEV_POPULATION_NAME_DESC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_SAMPLE_AID_ASC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_SAMPLE_AID_DESC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_SAMPLE_ID_ASC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_SAMPLE_ID_DESC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_SAMPLE_REASON_ASC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_SAMPLE_REASON_DESC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_SAMPLE_AMOUNT_ASC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_SAMPLE_AMOUNT_DESC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_SAMPLE_OWNER_ASC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_SAMPLE_OWNER_DESC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_SAMPLE_NAME_ASC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_SAMPLE_NAME_DESC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_POPULATION_AID_ASC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_POPULATION_AID_DESC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_POPULATION_ID_ASC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_POPULATION_ID_DESC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_POPULATION_REASON_ASC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_POPULATION_REASON_DESC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_POPULATION_AMOUNT_ASC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_POPULATION_AMOUNT_DESC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_POPULATION_OWNER_ASC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_POPULATION_OWNER_DESC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_POPULATION_NAME_ASC
  TOKEN_CANCELLEDS_BY_NAME_VARIANCE_POPULATION_NAME_DESC
}

"""
A filter to be used against `TokenClass` object types. All fields are combined with a logical ‘and.’
"""
input TokenClassFilter {
  """Filter by the object’s `contractAddress` field."""
  contractAddress: StringFilter

  """Filter by the object’s `minter` field."""
  minter: StringFilter

  """Filter by the object’s `class` field."""
  class: StringFilter

  """Filter by the object’s `name` field."""
  name: StringFilter

  """Filter by the object’s `description` field."""
  description: StringFilter

  """Filter by the object’s `image` field."""
  image: StringFilter

  """Filter by the object’s `type` field."""
  type: StringFilter

  """Filter by the object’s `cap` field."""
  cap: BigIntFilter

  """Filter by the object’s `supply` field."""
  supply: BigIntFilter

  """Filter by the object’s `paused` field."""
  paused: BooleanFilter

  """Filter by the object’s `stopped` field."""
  stopped: BooleanFilter

  """Filter by the object’s `tokensByName` relation."""
  tokensByName: TokenClassToManyTokenFilter

  """Some related `tokensByName` exist."""
  tokensByNameExist: Boolean

  """Filter by the object’s `tokenRetiredsByName` relation."""
  tokenRetiredsByName: TokenClassToManyTokenRetiredFilter

  """Some related `tokenRetiredsByName` exist."""
  tokenRetiredsByNameExist: Boolean

  """Filter by the object’s `tokenCancelledsByName` relation."""
  tokenCancelledsByName: TokenClassToManyTokenCancelledFilter

  """Some related `tokenCancelledsByName` exist."""
  tokenCancelledsByNameExist: Boolean

  """Filter by the object’s `entityByClass` relation."""
  entityByClass: EntityFilter

  """Checks for all expressions in this list."""
  and: [TokenClassFilter!]

  """Checks for any expressions in this list."""
  or: [TokenClassFilter!]

  """Negates the expression."""
  not: TokenClassFilter
}

"""
A filter to be used against many `TokenCancelled` object types. All fields are combined with a logical ‘and.’
"""
input TokenClassToManyTokenCancelledFilter {
  """
  Every related `TokenCancelled` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: TokenCancelledFilter

  """
  Some related `TokenCancelled` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: TokenCancelledFilter

  """
  No related `TokenCancelled` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: TokenCancelledFilter

  """Aggregates across related `TokenCancelled` match the filter criteria."""
  aggregates: TokenCancelledAggregatesFilter
}

"""
A filter to be used against many `Token` object types. All fields are combined with a logical ‘and.’
"""
input TokenClassToManyTokenFilter {
  """
  Every related `Token` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: TokenFilter

  """
  Some related `Token` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: TokenFilter

  """
  No related `Token` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: TokenFilter
}

"""
A filter to be used against many `TokenRetired` object types. All fields are combined with a logical ‘and.’
"""
input TokenClassToManyTokenRetiredFilter {
  """
  Every related `TokenRetired` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: TokenRetiredFilter

  """
  Some related `TokenRetired` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: TokenRetiredFilter

  """
  No related `TokenRetired` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: TokenRetiredFilter

  """Aggregates across related `TokenRetired` match the filter criteria."""
  aggregates: TokenRetiredAggregatesFilter
}

"""
A condition to be used against `Token` object types. All fields are tested for equality and combined with a logical ‘and.’
"""
input TokenCondition {
  """Checks for equality with the object’s `id` field."""
  id: String

  """Checks for equality with the object’s `index` field."""
  index: String

  """Checks for equality with the object’s `name` field."""
  name: String

  """Checks for equality with the object’s `collection` field."""
  collection: String
}

"""A connection to a list of `TokenDatum` values."""
type TokenDataConnection {
  """A list of `TokenDatum` objects."""
  nodes: [TokenDatum!]!

  """
  A list of edges which contains the `TokenDatum` and cursor to aid in pagination.
  """
  edges: [TokenDataEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `TokenDatum` you could get from the connection."""
  totalCount: Int!
}

"""A `TokenDatum` edge in the connection."""
type TokenDataEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `TokenDatum` at the end of the edge."""
  node: TokenDatum!
}

"""Methods to use when ordering `TokenDatum`."""
enum TokenDataOrderBy {
  NATURAL
  AID_ASC
  AID_DESC
  URI_ASC
  URI_DESC
  ENCRYPTED_ASC
  ENCRYPTED_DESC
  PROOF_ASC
  PROOF_DESC
  TYPE_ASC
  TYPE_DESC
  ID_ASC
  ID_DESC
  TOKEN_ID_ASC
  TOKEN_ID_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

type TokenDatum implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  aid: Int!
  uri: String!
  encrypted: Boolean!
  proof: String!
  type: String!
  id: String!
  tokenId: String!

  """Reads a single `Token` that is related to this `TokenDatum`."""
  token: Token
}

"""
A condition to be used against `TokenDatum` object types. All fields are tested
for equality and combined with a logical ‘and.’
"""
input TokenDatumCondition {
  """Checks for equality with the object’s `aid` field."""
  aid: Int

  """Checks for equality with the object’s `uri` field."""
  uri: String

  """Checks for equality with the object’s `encrypted` field."""
  encrypted: Boolean

  """Checks for equality with the object’s `proof` field."""
  proof: String

  """Checks for equality with the object’s `type` field."""
  type: String

  """Checks for equality with the object’s `id` field."""
  id: String

  """Checks for equality with the object’s `tokenId` field."""
  tokenId: String
}

"""
A filter to be used against `TokenDatum` object types. All fields are combined with a logical ‘and.’
"""
input TokenDatumFilter {
  """Filter by the object’s `aid` field."""
  aid: IntFilter

  """Filter by the object’s `uri` field."""
  uri: StringFilter

  """Filter by the object’s `encrypted` field."""
  encrypted: BooleanFilter

  """Filter by the object’s `proof` field."""
  proof: StringFilter

  """Filter by the object’s `type` field."""
  type: StringFilter

  """Filter by the object’s `id` field."""
  id: StringFilter

  """Filter by the object’s `tokenId` field."""
  tokenId: StringFilter

  """Filter by the object’s `token` relation."""
  token: TokenFilter

  """Checks for all expressions in this list."""
  and: [TokenDatumFilter!]

  """Checks for any expressions in this list."""
  or: [TokenDatumFilter!]

  """Negates the expression."""
  not: TokenDatumFilter
}

"""
A filter to be used against `Token` object types. All fields are combined with a logical ‘and.’
"""
input TokenFilter {
  """Filter by the object’s `id` field."""
  id: StringFilter

  """Filter by the object’s `index` field."""
  index: StringFilter

  """Filter by the object’s `name` field."""
  name: StringFilter

  """Filter by the object’s `collection` field."""
  collection: StringFilter

  """Filter by the object’s `tokenDataByTokenId` relation."""
  tokenDataByTokenId: TokenToManyTokenDatumFilter

  """Some related `tokenDataByTokenId` exist."""
  tokenDataByTokenIdExist: Boolean

  """Filter by the object’s `tokenRetiredsById` relation."""
  tokenRetiredsById: TokenToManyTokenRetiredFilter

  """Some related `tokenRetiredsById` exist."""
  tokenRetiredsByIdExist: Boolean

  """Filter by the object’s `tokenTransactionsByTokenId` relation."""
  tokenTransactionsByTokenId: TokenToManyTokenTransactionFilter

  """Some related `tokenTransactionsByTokenId` exist."""
  tokenTransactionsByTokenIdExist: Boolean

  """Filter by the object’s `tokenClassByName` relation."""
  tokenClassByName: TokenClassFilter

  """Filter by the object’s `entityByCollection` relation."""
  entityByCollection: EntityFilter

  """Checks for all expressions in this list."""
  and: [TokenFilter!]

  """Checks for any expressions in this list."""
  or: [TokenFilter!]

  """Negates the expression."""
  not: TokenFilter
}

type TokenomicsAccount implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  address: String!
  accountNumber: Int!
  availBalance: BigInt!
  delegationsBalance: BigInt!
  rewardsBalance: BigInt!
  totalBalance: BigInt!
  type: String
}

"""
A condition to be used against `TokenomicsAccount` object types. All fields are
tested for equality and combined with a logical ‘and.’
"""
input TokenomicsAccountCondition {
  """Checks for equality with the object’s `address` field."""
  address: String

  """Checks for equality with the object’s `accountNumber` field."""
  accountNumber: Int

  """Checks for equality with the object’s `availBalance` field."""
  availBalance: BigInt

  """Checks for equality with the object’s `delegationsBalance` field."""
  delegationsBalance: BigInt

  """Checks for equality with the object’s `rewardsBalance` field."""
  rewardsBalance: BigInt

  """Checks for equality with the object’s `totalBalance` field."""
  totalBalance: BigInt

  """Checks for equality with the object’s `type` field."""
  type: String
}

"""
A filter to be used against `TokenomicsAccount` object types. All fields are combined with a logical ‘and.’
"""
input TokenomicsAccountFilter {
  """Filter by the object’s `address` field."""
  address: StringFilter

  """Filter by the object’s `accountNumber` field."""
  accountNumber: IntFilter

  """Filter by the object’s `availBalance` field."""
  availBalance: BigIntFilter

  """Filter by the object’s `delegationsBalance` field."""
  delegationsBalance: BigIntFilter

  """Filter by the object’s `rewardsBalance` field."""
  rewardsBalance: BigIntFilter

  """Filter by the object’s `totalBalance` field."""
  totalBalance: BigIntFilter

  """Filter by the object’s `type` field."""
  type: StringFilter

  """Checks for all expressions in this list."""
  and: [TokenomicsAccountFilter!]

  """Checks for any expressions in this list."""
  or: [TokenomicsAccountFilter!]

  """Negates the expression."""
  not: TokenomicsAccountFilter
}

"""A connection to a list of `TokenomicsAccount` values."""
type TokenomicsAccountsConnection {
  """A list of `TokenomicsAccount` objects."""
  nodes: [TokenomicsAccount!]!

  """
  A list of edges which contains the `TokenomicsAccount` and cursor to aid in pagination.
  """
  edges: [TokenomicsAccountsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """
  The count of *all* `TokenomicsAccount` you could get from the connection.
  """
  totalCount: Int!
}

"""A `TokenomicsAccount` edge in the connection."""
type TokenomicsAccountsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `TokenomicsAccount` at the end of the edge."""
  node: TokenomicsAccount!
}

"""Methods to use when ordering `TokenomicsAccount`."""
enum TokenomicsAccountsOrderBy {
  NATURAL
  ADDRESS_ASC
  ADDRESS_DESC
  ACCOUNT_NUMBER_ASC
  ACCOUNT_NUMBER_DESC
  AVAIL_BALANCE_ASC
  AVAIL_BALANCE_DESC
  DELEGATIONS_BALANCE_ASC
  DELEGATIONS_BALANCE_DESC
  REWARDS_BALANCE_ASC
  REWARDS_BALANCE_DESC
  TOTAL_BALANCE_ASC
  TOTAL_BALANCE_DESC
  TYPE_ASC
  TYPE_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

type TokenRetired implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  aid: Int!
  id: String!
  reason: String!
  jurisdiction: String!
  amount: BigInt!
  owner: String!
  name: String!

  """Reads a single `Token` that is related to this `TokenRetired`."""
  tokenById: Token

  """Reads a single `TokenClass` that is related to this `TokenRetired`."""
  tokenClassByName: TokenClass
}

type TokenRetiredAggregates {
  keys: [String!]

  """
  Sum aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  sum: TokenRetiredSumAggregates

  """
  Distinct count aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  distinctCount: TokenRetiredDistinctCountAggregates

  """
  Minimum aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  min: TokenRetiredMinAggregates

  """
  Maximum aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  max: TokenRetiredMaxAggregates

  """
  Mean average aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  average: TokenRetiredAverageAggregates

  """
  Sample standard deviation aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  stddevSample: TokenRetiredStddevSampleAggregates

  """
  Population standard deviation aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  stddevPopulation: TokenRetiredStddevPopulationAggregates

  """
  Sample variance aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  varianceSample: TokenRetiredVarianceSampleAggregates

  """
  Population variance aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  variancePopulation: TokenRetiredVariancePopulationAggregates
}

"""A filter to be used against aggregates of `TokenRetired` object types."""
input TokenRetiredAggregatesFilter {
  """
  A filter that must pass for the relevant `TokenRetired` object to be included within the aggregate.
  """
  filter: TokenRetiredFilter

  """Sum aggregate over matching `TokenRetired` objects."""
  sum: TokenRetiredSumAggregateFilter

  """Distinct count aggregate over matching `TokenRetired` objects."""
  distinctCount: TokenRetiredDistinctCountAggregateFilter

  """Minimum aggregate over matching `TokenRetired` objects."""
  min: TokenRetiredMinAggregateFilter

  """Maximum aggregate over matching `TokenRetired` objects."""
  max: TokenRetiredMaxAggregateFilter

  """Mean average aggregate over matching `TokenRetired` objects."""
  average: TokenRetiredAverageAggregateFilter

  """
  Sample standard deviation aggregate over matching `TokenRetired` objects.
  """
  stddevSample: TokenRetiredStddevSampleAggregateFilter

  """
  Population standard deviation aggregate over matching `TokenRetired` objects.
  """
  stddevPopulation: TokenRetiredStddevPopulationAggregateFilter

  """Sample variance aggregate over matching `TokenRetired` objects."""
  varianceSample: TokenRetiredVarianceSampleAggregateFilter

  """Population variance aggregate over matching `TokenRetired` objects."""
  variancePopulation: TokenRetiredVariancePopulationAggregateFilter
}

input TokenRetiredAverageAggregateFilter {
  aid: BigFloatFilter
  amount: BigFloatFilter
}

type TokenRetiredAverageAggregates {
  """Mean average of aid across the matching connection"""
  aid: BigFloat

  """Mean average of amount across the matching connection"""
  amount: BigFloat
}

"""
A condition to be used against `TokenRetired` object types. All fields are
tested for equality and combined with a logical ‘and.’
"""
input TokenRetiredCondition {
  """Checks for equality with the object’s `aid` field."""
  aid: Int

  """Checks for equality with the object’s `id` field."""
  id: String

  """Checks for equality with the object’s `reason` field."""
  reason: String

  """Checks for equality with the object’s `jurisdiction` field."""
  jurisdiction: String

  """Checks for equality with the object’s `amount` field."""
  amount: BigInt

  """Checks for equality with the object’s `owner` field."""
  owner: String

  """Checks for equality with the object’s `name` field."""
  name: String
}

input TokenRetiredDistinctCountAggregateFilter {
  aid: BigIntFilter
  id: BigIntFilter
  reason: BigIntFilter
  jurisdiction: BigIntFilter
  amount: BigIntFilter
  owner: BigIntFilter
  name: BigIntFilter
}

type TokenRetiredDistinctCountAggregates {
  """Distinct count of aid across the matching connection"""
  aid: BigInt

  """Distinct count of id across the matching connection"""
  id: BigInt

  """Distinct count of reason across the matching connection"""
  reason: BigInt

  """Distinct count of jurisdiction across the matching connection"""
  jurisdiction: BigInt

  """Distinct count of amount across the matching connection"""
  amount: BigInt

  """Distinct count of owner across the matching connection"""
  owner: BigInt

  """Distinct count of name across the matching connection"""
  name: BigInt
}

"""
A filter to be used against `TokenRetired` object types. All fields are combined with a logical ‘and.’
"""
input TokenRetiredFilter {
  """Filter by the object’s `aid` field."""
  aid: IntFilter

  """Filter by the object’s `id` field."""
  id: StringFilter

  """Filter by the object’s `reason` field."""
  reason: StringFilter

  """Filter by the object’s `jurisdiction` field."""
  jurisdiction: StringFilter

  """Filter by the object’s `amount` field."""
  amount: BigIntFilter

  """Filter by the object’s `owner` field."""
  owner: StringFilter

  """Filter by the object’s `name` field."""
  name: StringFilter

  """Filter by the object’s `tokenById` relation."""
  tokenById: TokenFilter

  """Filter by the object’s `tokenClassByName` relation."""
  tokenClassByName: TokenClassFilter

  """Checks for all expressions in this list."""
  and: [TokenRetiredFilter!]

  """Checks for any expressions in this list."""
  or: [TokenRetiredFilter!]

  """Negates the expression."""
  not: TokenRetiredFilter
}

"""Grouping methods for `TokenRetired` for usage during aggregation."""
enum TokenRetiredGroupBy {
  ID
  REASON
  JURISDICTION
  AMOUNT
  OWNER
  NAME
}

input TokenRetiredHavingAverageInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenRetiredHavingDistinctCountInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

"""Conditions for `TokenRetired` aggregates."""
input TokenRetiredHavingInput {
  AND: [TokenRetiredHavingInput!]
  OR: [TokenRetiredHavingInput!]
  sum: TokenRetiredHavingSumInput
  distinctCount: TokenRetiredHavingDistinctCountInput
  min: TokenRetiredHavingMinInput
  max: TokenRetiredHavingMaxInput
  average: TokenRetiredHavingAverageInput
  stddevSample: TokenRetiredHavingStddevSampleInput
  stddevPopulation: TokenRetiredHavingStddevPopulationInput
  varianceSample: TokenRetiredHavingVarianceSampleInput
  variancePopulation: TokenRetiredHavingVariancePopulationInput
}

input TokenRetiredHavingMaxInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenRetiredHavingMinInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenRetiredHavingStddevPopulationInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenRetiredHavingStddevSampleInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenRetiredHavingSumInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenRetiredHavingVariancePopulationInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenRetiredHavingVarianceSampleInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenRetiredMaxAggregateFilter {
  aid: IntFilter
  amount: BigIntFilter
}

type TokenRetiredMaxAggregates {
  """Maximum of aid across the matching connection"""
  aid: Int

  """Maximum of amount across the matching connection"""
  amount: BigInt
}

input TokenRetiredMinAggregateFilter {
  aid: IntFilter
  amount: BigIntFilter
}

type TokenRetiredMinAggregates {
  """Minimum of aid across the matching connection"""
  aid: Int

  """Minimum of amount across the matching connection"""
  amount: BigInt
}

"""A connection to a list of `TokenRetired` values."""
type TokenRetiredsConnection {
  """A list of `TokenRetired` objects."""
  nodes: [TokenRetired!]!

  """
  A list of edges which contains the `TokenRetired` and cursor to aid in pagination.
  """
  edges: [TokenRetiredsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `TokenRetired` you could get from the connection."""
  totalCount: Int!

  """
  Aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  aggregates: TokenRetiredAggregates

  """
  Grouped aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  groupedAggregates(
    """The method to use when grouping `TokenRetired` for these aggregates."""
    groupBy: [TokenRetiredGroupBy!]!

    """Conditions on the grouped aggregates."""
    having: TokenRetiredHavingInput
  ): [TokenRetiredAggregates!]
}

"""A `TokenRetired` edge in the connection."""
type TokenRetiredsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `TokenRetired` at the end of the edge."""
  node: TokenRetired!
}

"""Methods to use when ordering `TokenRetired`."""
enum TokenRetiredsOrderBy {
  NATURAL
  AID_ASC
  AID_DESC
  ID_ASC
  ID_DESC
  REASON_ASC
  REASON_DESC
  JURISDICTION_ASC
  JURISDICTION_DESC
  AMOUNT_ASC
  AMOUNT_DESC
  OWNER_ASC
  OWNER_DESC
  NAME_ASC
  NAME_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

input TokenRetiredStddevPopulationAggregateFilter {
  aid: BigFloatFilter
  amount: BigFloatFilter
}

type TokenRetiredStddevPopulationAggregates {
  """Population standard deviation of aid across the matching connection"""
  aid: BigFloat

  """Population standard deviation of amount across the matching connection"""
  amount: BigFloat
}

input TokenRetiredStddevSampleAggregateFilter {
  aid: BigFloatFilter
  amount: BigFloatFilter
}

type TokenRetiredStddevSampleAggregates {
  """Sample standard deviation of aid across the matching connection"""
  aid: BigFloat

  """Sample standard deviation of amount across the matching connection"""
  amount: BigFloat
}

input TokenRetiredSumAggregateFilter {
  aid: BigIntFilter
  amount: BigFloatFilter
}

type TokenRetiredSumAggregates {
  """Sum of aid across the matching connection"""
  aid: BigInt!

  """Sum of amount across the matching connection"""
  amount: BigFloat!
}

input TokenRetiredVariancePopulationAggregateFilter {
  aid: BigFloatFilter
  amount: BigFloatFilter
}

type TokenRetiredVariancePopulationAggregates {
  """Population variance of aid across the matching connection"""
  aid: BigFloat

  """Population variance of amount across the matching connection"""
  amount: BigFloat
}

input TokenRetiredVarianceSampleAggregateFilter {
  aid: BigFloatFilter
  amount: BigFloatFilter
}

type TokenRetiredVarianceSampleAggregates {
  """Sample variance of aid across the matching connection"""
  aid: BigFloat

  """Sample variance of amount across the matching connection"""
  amount: BigFloat
}

"""A connection to a list of `Token` values."""
type TokensConnection {
  """A list of `Token` objects."""
  nodes: [Token!]!

  """
  A list of edges which contains the `Token` and cursor to aid in pagination.
  """
  edges: [TokensEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `Token` you could get from the connection."""
  totalCount: Int!
}

"""A `Token` edge in the connection."""
type TokensEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `Token` at the end of the edge."""
  node: Token!
}

"""Methods to use when ordering `Token`."""
enum TokensOrderBy {
  NATURAL
  ID_ASC
  ID_DESC
  INDEX_ASC
  INDEX_DESC
  NAME_ASC
  NAME_DESC
  COLLECTION_ASC
  COLLECTION_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
  TOKEN_RETIREDS_BY_ID_COUNT_ASC
  TOKEN_RETIREDS_BY_ID_COUNT_DESC
  TOKEN_RETIREDS_BY_ID_SUM_AID_ASC
  TOKEN_RETIREDS_BY_ID_SUM_AID_DESC
  TOKEN_RETIREDS_BY_ID_SUM_ID_ASC
  TOKEN_RETIREDS_BY_ID_SUM_ID_DESC
  TOKEN_RETIREDS_BY_ID_SUM_REASON_ASC
  TOKEN_RETIREDS_BY_ID_SUM_REASON_DESC
  TOKEN_RETIREDS_BY_ID_SUM_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_ID_SUM_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_ID_SUM_AMOUNT_ASC
  TOKEN_RETIREDS_BY_ID_SUM_AMOUNT_DESC
  TOKEN_RETIREDS_BY_ID_SUM_OWNER_ASC
  TOKEN_RETIREDS_BY_ID_SUM_OWNER_DESC
  TOKEN_RETIREDS_BY_ID_SUM_NAME_ASC
  TOKEN_RETIREDS_BY_ID_SUM_NAME_DESC
  TOKEN_RETIREDS_BY_ID_DISTINCT_COUNT_AID_ASC
  TOKEN_RETIREDS_BY_ID_DISTINCT_COUNT_AID_DESC
  TOKEN_RETIREDS_BY_ID_DISTINCT_COUNT_ID_ASC
  TOKEN_RETIREDS_BY_ID_DISTINCT_COUNT_ID_DESC
  TOKEN_RETIREDS_BY_ID_DISTINCT_COUNT_REASON_ASC
  TOKEN_RETIREDS_BY_ID_DISTINCT_COUNT_REASON_DESC
  TOKEN_RETIREDS_BY_ID_DISTINCT_COUNT_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_ID_DISTINCT_COUNT_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_ID_DISTINCT_COUNT_AMOUNT_ASC
  TOKEN_RETIREDS_BY_ID_DISTINCT_COUNT_AMOUNT_DESC
  TOKEN_RETIREDS_BY_ID_DISTINCT_COUNT_OWNER_ASC
  TOKEN_RETIREDS_BY_ID_DISTINCT_COUNT_OWNER_DESC
  TOKEN_RETIREDS_BY_ID_DISTINCT_COUNT_NAME_ASC
  TOKEN_RETIREDS_BY_ID_DISTINCT_COUNT_NAME_DESC
  TOKEN_RETIREDS_BY_ID_MIN_AID_ASC
  TOKEN_RETIREDS_BY_ID_MIN_AID_DESC
  TOKEN_RETIREDS_BY_ID_MIN_ID_ASC
  TOKEN_RETIREDS_BY_ID_MIN_ID_DESC
  TOKEN_RETIREDS_BY_ID_MIN_REASON_ASC
  TOKEN_RETIREDS_BY_ID_MIN_REASON_DESC
  TOKEN_RETIREDS_BY_ID_MIN_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_ID_MIN_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_ID_MIN_AMOUNT_ASC
  TOKEN_RETIREDS_BY_ID_MIN_AMOUNT_DESC
  TOKEN_RETIREDS_BY_ID_MIN_OWNER_ASC
  TOKEN_RETIREDS_BY_ID_MIN_OWNER_DESC
  TOKEN_RETIREDS_BY_ID_MIN_NAME_ASC
  TOKEN_RETIREDS_BY_ID_MIN_NAME_DESC
  TOKEN_RETIREDS_BY_ID_MAX_AID_ASC
  TOKEN_RETIREDS_BY_ID_MAX_AID_DESC
  TOKEN_RETIREDS_BY_ID_MAX_ID_ASC
  TOKEN_RETIREDS_BY_ID_MAX_ID_DESC
  TOKEN_RETIREDS_BY_ID_MAX_REASON_ASC
  TOKEN_RETIREDS_BY_ID_MAX_REASON_DESC
  TOKEN_RETIREDS_BY_ID_MAX_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_ID_MAX_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_ID_MAX_AMOUNT_ASC
  TOKEN_RETIREDS_BY_ID_MAX_AMOUNT_DESC
  TOKEN_RETIREDS_BY_ID_MAX_OWNER_ASC
  TOKEN_RETIREDS_BY_ID_MAX_OWNER_DESC
  TOKEN_RETIREDS_BY_ID_MAX_NAME_ASC
  TOKEN_RETIREDS_BY_ID_MAX_NAME_DESC
  TOKEN_RETIREDS_BY_ID_AVERAGE_AID_ASC
  TOKEN_RETIREDS_BY_ID_AVERAGE_AID_DESC
  TOKEN_RETIREDS_BY_ID_AVERAGE_ID_ASC
  TOKEN_RETIREDS_BY_ID_AVERAGE_ID_DESC
  TOKEN_RETIREDS_BY_ID_AVERAGE_REASON_ASC
  TOKEN_RETIREDS_BY_ID_AVERAGE_REASON_DESC
  TOKEN_RETIREDS_BY_ID_AVERAGE_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_ID_AVERAGE_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_ID_AVERAGE_AMOUNT_ASC
  TOKEN_RETIREDS_BY_ID_AVERAGE_AMOUNT_DESC
  TOKEN_RETIREDS_BY_ID_AVERAGE_OWNER_ASC
  TOKEN_RETIREDS_BY_ID_AVERAGE_OWNER_DESC
  TOKEN_RETIREDS_BY_ID_AVERAGE_NAME_ASC
  TOKEN_RETIREDS_BY_ID_AVERAGE_NAME_DESC
  TOKEN_RETIREDS_BY_ID_STDDEV_SAMPLE_AID_ASC
  TOKEN_RETIREDS_BY_ID_STDDEV_SAMPLE_AID_DESC
  TOKEN_RETIREDS_BY_ID_STDDEV_SAMPLE_ID_ASC
  TOKEN_RETIREDS_BY_ID_STDDEV_SAMPLE_ID_DESC
  TOKEN_RETIREDS_BY_ID_STDDEV_SAMPLE_REASON_ASC
  TOKEN_RETIREDS_BY_ID_STDDEV_SAMPLE_REASON_DESC
  TOKEN_RETIREDS_BY_ID_STDDEV_SAMPLE_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_ID_STDDEV_SAMPLE_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_ID_STDDEV_SAMPLE_AMOUNT_ASC
  TOKEN_RETIREDS_BY_ID_STDDEV_SAMPLE_AMOUNT_DESC
  TOKEN_RETIREDS_BY_ID_STDDEV_SAMPLE_OWNER_ASC
  TOKEN_RETIREDS_BY_ID_STDDEV_SAMPLE_OWNER_DESC
  TOKEN_RETIREDS_BY_ID_STDDEV_SAMPLE_NAME_ASC
  TOKEN_RETIREDS_BY_ID_STDDEV_SAMPLE_NAME_DESC
  TOKEN_RETIREDS_BY_ID_STDDEV_POPULATION_AID_ASC
  TOKEN_RETIREDS_BY_ID_STDDEV_POPULATION_AID_DESC
  TOKEN_RETIREDS_BY_ID_STDDEV_POPULATION_ID_ASC
  TOKEN_RETIREDS_BY_ID_STDDEV_POPULATION_ID_DESC
  TOKEN_RETIREDS_BY_ID_STDDEV_POPULATION_REASON_ASC
  TOKEN_RETIREDS_BY_ID_STDDEV_POPULATION_REASON_DESC
  TOKEN_RETIREDS_BY_ID_STDDEV_POPULATION_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_ID_STDDEV_POPULATION_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_ID_STDDEV_POPULATION_AMOUNT_ASC
  TOKEN_RETIREDS_BY_ID_STDDEV_POPULATION_AMOUNT_DESC
  TOKEN_RETIREDS_BY_ID_STDDEV_POPULATION_OWNER_ASC
  TOKEN_RETIREDS_BY_ID_STDDEV_POPULATION_OWNER_DESC
  TOKEN_RETIREDS_BY_ID_STDDEV_POPULATION_NAME_ASC
  TOKEN_RETIREDS_BY_ID_STDDEV_POPULATION_NAME_DESC
  TOKEN_RETIREDS_BY_ID_VARIANCE_SAMPLE_AID_ASC
  TOKEN_RETIREDS_BY_ID_VARIANCE_SAMPLE_AID_DESC
  TOKEN_RETIREDS_BY_ID_VARIANCE_SAMPLE_ID_ASC
  TOKEN_RETIREDS_BY_ID_VARIANCE_SAMPLE_ID_DESC
  TOKEN_RETIREDS_BY_ID_VARIANCE_SAMPLE_REASON_ASC
  TOKEN_RETIREDS_BY_ID_VARIANCE_SAMPLE_REASON_DESC
  TOKEN_RETIREDS_BY_ID_VARIANCE_SAMPLE_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_ID_VARIANCE_SAMPLE_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_ID_VARIANCE_SAMPLE_AMOUNT_ASC
  TOKEN_RETIREDS_BY_ID_VARIANCE_SAMPLE_AMOUNT_DESC
  TOKEN_RETIREDS_BY_ID_VARIANCE_SAMPLE_OWNER_ASC
  TOKEN_RETIREDS_BY_ID_VARIANCE_SAMPLE_OWNER_DESC
  TOKEN_RETIREDS_BY_ID_VARIANCE_SAMPLE_NAME_ASC
  TOKEN_RETIREDS_BY_ID_VARIANCE_SAMPLE_NAME_DESC
  TOKEN_RETIREDS_BY_ID_VARIANCE_POPULATION_AID_ASC
  TOKEN_RETIREDS_BY_ID_VARIANCE_POPULATION_AID_DESC
  TOKEN_RETIREDS_BY_ID_VARIANCE_POPULATION_ID_ASC
  TOKEN_RETIREDS_BY_ID_VARIANCE_POPULATION_ID_DESC
  TOKEN_RETIREDS_BY_ID_VARIANCE_POPULATION_REASON_ASC
  TOKEN_RETIREDS_BY_ID_VARIANCE_POPULATION_REASON_DESC
  TOKEN_RETIREDS_BY_ID_VARIANCE_POPULATION_JURISDICTION_ASC
  TOKEN_RETIREDS_BY_ID_VARIANCE_POPULATION_JURISDICTION_DESC
  TOKEN_RETIREDS_BY_ID_VARIANCE_POPULATION_AMOUNT_ASC
  TOKEN_RETIREDS_BY_ID_VARIANCE_POPULATION_AMOUNT_DESC
  TOKEN_RETIREDS_BY_ID_VARIANCE_POPULATION_OWNER_ASC
  TOKEN_RETIREDS_BY_ID_VARIANCE_POPULATION_OWNER_DESC
  TOKEN_RETIREDS_BY_ID_VARIANCE_POPULATION_NAME_ASC
  TOKEN_RETIREDS_BY_ID_VARIANCE_POPULATION_NAME_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_COUNT_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_COUNT_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_SUM_AID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_SUM_AID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_SUM_FROM_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_SUM_FROM_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_SUM_TO_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_SUM_TO_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_SUM_AMOUNT_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_SUM_AMOUNT_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_SUM_TOKEN_ID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_SUM_TOKEN_ID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_DISTINCT_COUNT_AID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_DISTINCT_COUNT_AID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_DISTINCT_COUNT_FROM_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_DISTINCT_COUNT_FROM_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_DISTINCT_COUNT_TO_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_DISTINCT_COUNT_TO_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_DISTINCT_COUNT_AMOUNT_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_DISTINCT_COUNT_AMOUNT_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_DISTINCT_COUNT_TOKEN_ID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_DISTINCT_COUNT_TOKEN_ID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MIN_AID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MIN_AID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MIN_FROM_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MIN_FROM_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MIN_TO_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MIN_TO_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MIN_AMOUNT_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MIN_AMOUNT_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MIN_TOKEN_ID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MIN_TOKEN_ID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MAX_AID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MAX_AID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MAX_FROM_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MAX_FROM_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MAX_TO_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MAX_TO_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MAX_AMOUNT_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MAX_AMOUNT_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MAX_TOKEN_ID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_MAX_TOKEN_ID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_AVERAGE_AID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_AVERAGE_AID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_AVERAGE_FROM_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_AVERAGE_FROM_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_AVERAGE_TO_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_AVERAGE_TO_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_AVERAGE_AMOUNT_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_AVERAGE_AMOUNT_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_AVERAGE_TOKEN_ID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_AVERAGE_TOKEN_ID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_SAMPLE_AID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_SAMPLE_AID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_SAMPLE_FROM_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_SAMPLE_FROM_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_SAMPLE_TO_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_SAMPLE_TO_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_SAMPLE_AMOUNT_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_SAMPLE_AMOUNT_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_SAMPLE_TOKEN_ID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_SAMPLE_TOKEN_ID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_POPULATION_AID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_POPULATION_AID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_POPULATION_FROM_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_POPULATION_FROM_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_POPULATION_TO_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_POPULATION_TO_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_POPULATION_AMOUNT_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_POPULATION_AMOUNT_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_POPULATION_TOKEN_ID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_STDDEV_POPULATION_TOKEN_ID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_SAMPLE_AID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_SAMPLE_AID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_SAMPLE_FROM_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_SAMPLE_FROM_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_SAMPLE_TO_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_SAMPLE_TO_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_SAMPLE_AMOUNT_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_SAMPLE_AMOUNT_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_SAMPLE_TOKEN_ID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_SAMPLE_TOKEN_ID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_POPULATION_AID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_POPULATION_AID_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_POPULATION_FROM_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_POPULATION_FROM_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_POPULATION_TO_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_POPULATION_TO_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_POPULATION_AMOUNT_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_POPULATION_AMOUNT_DESC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_POPULATION_TOKEN_ID_ASC
  TOKEN_TRANSACTIONS_BY_TOKEN_ID_VARIANCE_POPULATION_TOKEN_ID_DESC
}

"""
A filter to be used against many `TokenDatum` object types. All fields are combined with a logical ‘and.’
"""
input TokenToManyTokenDatumFilter {
  """
  Every related `TokenDatum` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: TokenDatumFilter

  """
  Some related `TokenDatum` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: TokenDatumFilter

  """
  No related `TokenDatum` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: TokenDatumFilter
}

"""
A filter to be used against many `TokenRetired` object types. All fields are combined with a logical ‘and.’
"""
input TokenToManyTokenRetiredFilter {
  """
  Every related `TokenRetired` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: TokenRetiredFilter

  """
  Some related `TokenRetired` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: TokenRetiredFilter

  """
  No related `TokenRetired` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: TokenRetiredFilter

  """Aggregates across related `TokenRetired` match the filter criteria."""
  aggregates: TokenRetiredAggregatesFilter
}

"""
A filter to be used against many `TokenTransaction` object types. All fields are combined with a logical ‘and.’
"""
input TokenToManyTokenTransactionFilter {
  """
  Every related `TokenTransaction` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: TokenTransactionFilter

  """
  Some related `TokenTransaction` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: TokenTransactionFilter

  """
  No related `TokenTransaction` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: TokenTransactionFilter

  """
  Aggregates across related `TokenTransaction` match the filter criteria.
  """
  aggregates: TokenTransactionAggregatesFilter
}

type TokenTransaction implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  aid: Int!
  from: String!
  to: String!
  amount: BigInt!
  tokenId: String!

  """Reads a single `Token` that is related to this `TokenTransaction`."""
  token: Token
}

type TokenTransactionAggregates {
  keys: [String!]

  """
  Sum aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  sum: TokenTransactionSumAggregates

  """
  Distinct count aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  distinctCount: TokenTransactionDistinctCountAggregates

  """
  Minimum aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  min: TokenTransactionMinAggregates

  """
  Maximum aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  max: TokenTransactionMaxAggregates

  """
  Mean average aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  average: TokenTransactionAverageAggregates

  """
  Sample standard deviation aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  stddevSample: TokenTransactionStddevSampleAggregates

  """
  Population standard deviation aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  stddevPopulation: TokenTransactionStddevPopulationAggregates

  """
  Sample variance aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  varianceSample: TokenTransactionVarianceSampleAggregates

  """
  Population variance aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  variancePopulation: TokenTransactionVariancePopulationAggregates
}

"""
A filter to be used against aggregates of `TokenTransaction` object types.
"""
input TokenTransactionAggregatesFilter {
  """
  A filter that must pass for the relevant `TokenTransaction` object to be included within the aggregate.
  """
  filter: TokenTransactionFilter

  """Sum aggregate over matching `TokenTransaction` objects."""
  sum: TokenTransactionSumAggregateFilter

  """Distinct count aggregate over matching `TokenTransaction` objects."""
  distinctCount: TokenTransactionDistinctCountAggregateFilter

  """Minimum aggregate over matching `TokenTransaction` objects."""
  min: TokenTransactionMinAggregateFilter

  """Maximum aggregate over matching `TokenTransaction` objects."""
  max: TokenTransactionMaxAggregateFilter

  """Mean average aggregate over matching `TokenTransaction` objects."""
  average: TokenTransactionAverageAggregateFilter

  """
  Sample standard deviation aggregate over matching `TokenTransaction` objects.
  """
  stddevSample: TokenTransactionStddevSampleAggregateFilter

  """
  Population standard deviation aggregate over matching `TokenTransaction` objects.
  """
  stddevPopulation: TokenTransactionStddevPopulationAggregateFilter

  """Sample variance aggregate over matching `TokenTransaction` objects."""
  varianceSample: TokenTransactionVarianceSampleAggregateFilter

  """
  Population variance aggregate over matching `TokenTransaction` objects.
  """
  variancePopulation: TokenTransactionVariancePopulationAggregateFilter
}

input TokenTransactionAverageAggregateFilter {
  aid: BigFloatFilter
  amount: BigFloatFilter
}

type TokenTransactionAverageAggregates {
  """Mean average of aid across the matching connection"""
  aid: BigFloat

  """Mean average of amount across the matching connection"""
  amount: BigFloat
}

"""
A condition to be used against `TokenTransaction` object types. All fields are
tested for equality and combined with a logical ‘and.’
"""
input TokenTransactionCondition {
  """Checks for equality with the object’s `aid` field."""
  aid: Int

  """Checks for equality with the object’s `from` field."""
  from: String

  """Checks for equality with the object’s `to` field."""
  to: String

  """Checks for equality with the object’s `amount` field."""
  amount: BigInt

  """Checks for equality with the object’s `tokenId` field."""
  tokenId: String
}

input TokenTransactionDistinctCountAggregateFilter {
  aid: BigIntFilter
  from: BigIntFilter
  to: BigIntFilter
  amount: BigIntFilter
  tokenId: BigIntFilter
}

type TokenTransactionDistinctCountAggregates {
  """Distinct count of aid across the matching connection"""
  aid: BigInt

  """Distinct count of from across the matching connection"""
  from: BigInt

  """Distinct count of to across the matching connection"""
  to: BigInt

  """Distinct count of amount across the matching connection"""
  amount: BigInt

  """Distinct count of tokenId across the matching connection"""
  tokenId: BigInt
}

"""
A filter to be used against `TokenTransaction` object types. All fields are combined with a logical ‘and.’
"""
input TokenTransactionFilter {
  """Filter by the object’s `aid` field."""
  aid: IntFilter

  """Filter by the object’s `from` field."""
  from: StringFilter

  """Filter by the object’s `to` field."""
  to: StringFilter

  """Filter by the object’s `amount` field."""
  amount: BigIntFilter

  """Filter by the object’s `tokenId` field."""
  tokenId: StringFilter

  """Filter by the object’s `token` relation."""
  token: TokenFilter

  """Checks for all expressions in this list."""
  and: [TokenTransactionFilter!]

  """Checks for any expressions in this list."""
  or: [TokenTransactionFilter!]

  """Negates the expression."""
  not: TokenTransactionFilter
}

"""Grouping methods for `TokenTransaction` for usage during aggregation."""
enum TokenTransactionGroupBy {
  FROM
  TO
  AMOUNT
  TOKEN_ID
}

input TokenTransactionHavingAverageInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenTransactionHavingDistinctCountInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

"""Conditions for `TokenTransaction` aggregates."""
input TokenTransactionHavingInput {
  AND: [TokenTransactionHavingInput!]
  OR: [TokenTransactionHavingInput!]
  sum: TokenTransactionHavingSumInput
  distinctCount: TokenTransactionHavingDistinctCountInput
  min: TokenTransactionHavingMinInput
  max: TokenTransactionHavingMaxInput
  average: TokenTransactionHavingAverageInput
  stddevSample: TokenTransactionHavingStddevSampleInput
  stddevPopulation: TokenTransactionHavingStddevPopulationInput
  varianceSample: TokenTransactionHavingVarianceSampleInput
  variancePopulation: TokenTransactionHavingVariancePopulationInput
}

input TokenTransactionHavingMaxInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenTransactionHavingMinInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenTransactionHavingStddevPopulationInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenTransactionHavingStddevSampleInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenTransactionHavingSumInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenTransactionHavingVariancePopulationInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenTransactionHavingVarianceSampleInput {
  aid: HavingIntFilter
  amount: HavingBigintFilter
}

input TokenTransactionMaxAggregateFilter {
  aid: IntFilter
  amount: BigIntFilter
}

type TokenTransactionMaxAggregates {
  """Maximum of aid across the matching connection"""
  aid: Int

  """Maximum of amount across the matching connection"""
  amount: BigInt
}

input TokenTransactionMinAggregateFilter {
  aid: IntFilter
  amount: BigIntFilter
}

type TokenTransactionMinAggregates {
  """Minimum of aid across the matching connection"""
  aid: Int

  """Minimum of amount across the matching connection"""
  amount: BigInt
}

"""A connection to a list of `TokenTransaction` values."""
type TokenTransactionsConnection {
  """A list of `TokenTransaction` objects."""
  nodes: [TokenTransaction!]!

  """
  A list of edges which contains the `TokenTransaction` and cursor to aid in pagination.
  """
  edges: [TokenTransactionsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """
  The count of *all* `TokenTransaction` you could get from the connection.
  """
  totalCount: Int!

  """
  Aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  aggregates: TokenTransactionAggregates

  """
  Grouped aggregates across the matching connection (ignoring before/after/first/last/offset)
  """
  groupedAggregates(
    """
    The method to use when grouping `TokenTransaction` for these aggregates.
    """
    groupBy: [TokenTransactionGroupBy!]!

    """Conditions on the grouped aggregates."""
    having: TokenTransactionHavingInput
  ): [TokenTransactionAggregates!]
}

"""A `TokenTransaction` edge in the connection."""
type TokenTransactionsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `TokenTransaction` at the end of the edge."""
  node: TokenTransaction!
}

"""Methods to use when ordering `TokenTransaction`."""
enum TokenTransactionsOrderBy {
  NATURAL
  AID_ASC
  AID_DESC
  FROM_ASC
  FROM_DESC
  TO_ASC
  TO_DESC
  AMOUNT_ASC
  AMOUNT_DESC
  TOKEN_ID_ASC
  TOKEN_ID_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

input TokenTransactionStddevPopulationAggregateFilter {
  aid: BigFloatFilter
  amount: BigFloatFilter
}

type TokenTransactionStddevPopulationAggregates {
  """Population standard deviation of aid across the matching connection"""
  aid: BigFloat

  """Population standard deviation of amount across the matching connection"""
  amount: BigFloat
}

input TokenTransactionStddevSampleAggregateFilter {
  aid: BigFloatFilter
  amount: BigFloatFilter
}

type TokenTransactionStddevSampleAggregates {
  """Sample standard deviation of aid across the matching connection"""
  aid: BigFloat

  """Sample standard deviation of amount across the matching connection"""
  amount: BigFloat
}

input TokenTransactionSumAggregateFilter {
  aid: BigIntFilter
  amount: BigFloatFilter
}

type TokenTransactionSumAggregates {
  """Sum of aid across the matching connection"""
  aid: BigInt!

  """Sum of amount across the matching connection"""
  amount: BigFloat!
}

input TokenTransactionVariancePopulationAggregateFilter {
  aid: BigFloatFilter
  amount: BigFloatFilter
}

type TokenTransactionVariancePopulationAggregates {
  """Population variance of aid across the matching connection"""
  aid: BigFloat

  """Population variance of amount across the matching connection"""
  amount: BigFloat
}

input TokenTransactionVarianceSampleAggregateFilter {
  aid: BigFloatFilter
  amount: BigFloatFilter
}

type TokenTransactionVarianceSampleAggregates {
  """Sample variance of aid across the matching connection"""
  aid: BigFloat

  """Sample variance of amount across the matching connection"""
  amount: BigFloat
}

type Transaction implements Node {
  """
  A globally unique identifier. Can be used in various places throughout the system to identify this single value.
  """
  nodeId: ID!
  hash: String!
  height: Int!
  code: Int!
  fee: JSON!
  gasUsed: String!
  gasWanted: String!
  time: Datetime!
  memo: String!

  """Reads and enables pagination through a set of `Message`."""
  messagesByTransactionHash(
    """Only read the first `n` values of the set."""
    first: Int

    """Only read the last `n` values of the set."""
    last: Int

    """
    Skip the first `n` values from our `after` cursor, an alternative to cursor
    based pagination. May not be used with `last`.
    """
    offset: Int

    """Read all values in the set before (above) this cursor."""
    before: Cursor

    """Read all values in the set after (below) this cursor."""
    after: Cursor

    """The method to use when ordering `Message`."""
    orderBy: [MessagesOrderBy!] = [PRIMARY_KEY_ASC]

    """
    A condition to be used in determining which values should be returned by the collection.
    """
    condition: MessageCondition

    """
    A filter to be used in determining which values should be returned by the collection.
    """
    filter: MessageFilter
  ): MessagesConnection!
}

"""
A condition to be used against `Transaction` object types. All fields are tested
for equality and combined with a logical ‘and.’
"""
input TransactionCondition {
  """Checks for equality with the object’s `hash` field."""
  hash: String

  """Checks for equality with the object’s `height` field."""
  height: Int

  """Checks for equality with the object’s `code` field."""
  code: Int

  """Checks for equality with the object’s `fee` field."""
  fee: JSON

  """Checks for equality with the object’s `gasUsed` field."""
  gasUsed: String

  """Checks for equality with the object’s `gasWanted` field."""
  gasWanted: String

  """Checks for equality with the object’s `time` field."""
  time: Datetime

  """Checks for equality with the object’s `memo` field."""
  memo: String
}

"""
A filter to be used against `Transaction` object types. All fields are combined with a logical ‘and.’
"""
input TransactionFilter {
  """Filter by the object’s `hash` field."""
  hash: StringFilter

  """Filter by the object’s `height` field."""
  height: IntFilter

  """Filter by the object’s `code` field."""
  code: IntFilter

  """Filter by the object’s `fee` field."""
  fee: JSONFilter

  """Filter by the object’s `gasUsed` field."""
  gasUsed: StringFilter

  """Filter by the object’s `gasWanted` field."""
  gasWanted: StringFilter

  """Filter by the object’s `time` field."""
  time: DatetimeFilter

  """Filter by the object’s `memo` field."""
  memo: StringFilter

  """Filter by the object’s `messagesByTransactionHash` relation."""
  messagesByTransactionHash: TransactionToManyMessageFilter

  """Some related `messagesByTransactionHash` exist."""
  messagesByTransactionHashExist: Boolean

  """Checks for all expressions in this list."""
  and: [TransactionFilter!]

  """Checks for any expressions in this list."""
  or: [TransactionFilter!]

  """Negates the expression."""
  not: TransactionFilter
}

"""A connection to a list of `Transaction` values."""
type TransactionsConnection {
  """A list of `Transaction` objects."""
  nodes: [Transaction!]!

  """
  A list of edges which contains the `Transaction` and cursor to aid in pagination.
  """
  edges: [TransactionsEdge!]!

  """Information to aid in pagination."""
  pageInfo: PageInfo!

  """The count of *all* `Transaction` you could get from the connection."""
  totalCount: Int!
}

"""A `Transaction` edge in the connection."""
type TransactionsEdge {
  """A cursor for use in pagination."""
  cursor: Cursor

  """The `Transaction` at the end of the edge."""
  node: Transaction!
}

"""Methods to use when ordering `Transaction`."""
enum TransactionsOrderBy {
  NATURAL
  HASH_ASC
  HASH_DESC
  HEIGHT_ASC
  HEIGHT_DESC
  CODE_ASC
  CODE_DESC
  FEE_ASC
  FEE_DESC
  GAS_USED_ASC
  GAS_USED_DESC
  GAS_WANTED_ASC
  GAS_WANTED_DESC
  TIME_ASC
  TIME_DESC
  MEMO_ASC
  MEMO_DESC
  PRIMARY_KEY_ASC
  PRIMARY_KEY_DESC
}

"""
A filter to be used against many `Message` object types. All fields are combined with a logical ‘and.’
"""
input TransactionToManyMessageFilter {
  """
  Every related `Message` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  every: MessageFilter

  """
  Some related `Message` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  some: MessageFilter

  """
  No related `Message` matches the filter criteria. All fields are combined with a logical ‘and.’
  """
  none: MessageFilter
}
``