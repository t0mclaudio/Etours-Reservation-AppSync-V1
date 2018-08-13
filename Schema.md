input CreateReservationInput {
	email: String!
	name: String!
	contact: String!
	notes: String
	tour_code: String!
	inquiry_date: String!
	start_date: String!
	tour_date: String!
	end_date: String!
	option_date: String!
	adults: Int!
	k02: Int!
	k35: Int!
	k61: Int!
	adult_price: Float!
	k02_price: Float!
	k35_price: Float!
	k61_price: Float!
	adult_total: Float!
	k02_total: Float!
	k35_total: Float!
	k61_total: Float!
	total: Float!
	downpayment: Float!
	balance: Float!
}

# input DeleteReservationInput {
#### 	id: ID!
#### }
type Mutation {
	createReservation(input: CreateReservationInput!): Reservation
	updateReservation(input: UpdateReservationInput!): Reservation
}

type Query {
	getReservation(id: ID!): Reservation
	listReservations(filter: TableReservationFilterInput, limit: Int, nextToken: String): ReservationConnection
	queryReservationsByEmailDateCreated(email: String!, first: Int, after: String): ReservationConnection
}

type Reservation {
	id: ID!
	name: String!
	email: String!
	date_created: String!
	contact: String!
	notes: String
	tour_code: String!
	inquiry_date: String!
	tour_date: String!
	end_date: String!
	option_date: String!
	adults: Int!
	k02: Int!
	k35: Int!
	k61: Int!
	adult_price: Float!
	k02_price: Float!
	k35_price: Float!
	k61_price: Float!
	adult_total: Float!
	k02_total: Float!
	k35_total: Float!
	k61_total: Float!
	total: Float!
	downpayment: Float!
	balance: Float!
	status: Status!
}

type ReservationConnection {
	items: [Reservation]
	nextToken: String
}

enum Status {
	Pending
	Sent
	Paid
}

type Subscription {
	onCreateReservation(id: ID, email: String, date_created: String): Reservation
		@aws_subscribe(mutations: ["createReservation"])
	onUpdateReservation(id: ID, email: String, date_created: String): Reservation
		@aws_subscribe(mutations: ["updateReservation"])
}

input TableBooleanFilterInput {
	ne: Boolean
	eq: Boolean
}

input TableFloatFilterInput {
	ne: Float
	eq: Float
	le: Float
	lt: Float
	ge: Float
	gt: Float
	contains: Float
	notContains: Float
	between: [Float]
}

input TableIDFilterInput {
	ne: ID
	eq: ID
	le: ID
	lt: ID
	ge: ID
	gt: ID
	contains: ID
	notContains: ID
	between: [ID]
	beginsWith: ID
}

input TableIntFilterInput {
	ne: Int
	eq: Int
	le: Int
	lt: Int
	ge: Int
	gt: Int
	contains: Int
	notContains: Int
	between: [Int]
}

input TableReservationFilterInput {
	id: TableIDFilterInput
	email: TableStringFilterInput
	date_created: TableStringFilterInput
}

input TableStringFilterInput {
	ne: String
	eq: String
	le: String
	lt: String
	ge: String
	gt: String
	contains: String
	notContains: String
	between: [String]
	beginsWith: String
}

input UpdateReservationInput {
	id: ID!
	email: String
	date_created: String
}