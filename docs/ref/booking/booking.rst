booking/[booking_id]
====================
.. http:method:: GET /api/3.0/booking/{booking_id}

	:arg string booking_id: The unique booking code identifying a booking in the system.
	
.. http:response:: Retrieve extended information on a specific booking.

booking/[booking_id]/invoice
----------------------------
.. http:method:: GET /api/3.0/booking/{booking_id}/invoice

	:arg string booking_id: The unique booking code identifying a booking in the system.
	
.. http:response:: Return a pre-formatted invoice to display to the customer.

booking/[booking_id]/checkin
----------------------------
You can check-in and check-out a booking.  By default, a note is created under the name of the account when a booking is either checked in or checked out.  VOID, and CANCELLED bookings cannot be checked-in or out.

.. http:method:: POST /api/3.0/booking/{booking_id}/checkin

	:arg string booking_id: The unique booking code identifying a booking in the system.

booking/[booking_id]/checkout
-----------------------------

.. http:method:: POST /api/3.0/booking/{booking_id}/checkout

	:arg string booking_id: The unique booking code identifying a booking in the system.


booking/[booking_id]/update
---------------------------

The state of an existing booking can be modified using calls to booking/update.

Specifying the ``status_id`` is **required**, but any other update fields are optional.

.. http:method:: POST /api/3.0/booking/{booking_id}/update

	:arg string booking_id: The unique booking code identifying a booking in the system.
	:param string status_id: The status that this booking should be set to. See **Manage / Layout / Statuses** in your account for a list of all available statuses. The default available statuses are: **PEND, HOLD, PART, PAID, WAIT, STOP,** and **VOID**
	
	:optparam boolean notify: Toggle whether to trigger notifications when this booking is changed. (default: 1)
	:optparam boolean set_paid: When set to **1** (true) on an *unpaid* booking, and the requested status_id is '**PAID**', attempt to create a POS transaction covering the remaining cost of the booking (cannot be used with other input).

	.. literalinclude:: ../examples/response/booking-index.json
		:language: js
		:linenos:

booking/[booking_id]/bookmark
-----------------------------

Bookmarks are made available in the Checkfront mobile apps, and are listed under bookings while logged into the platform.  You can add or remove a bookmark to a specific booking for the account you are acting on behalf of.

.. http:method:: POST /api/3.0/booking/{booking_id}/bookmark

	:arg string booking_id: The unique booking code identifying a booking in the system.
	:param boolean mark: Enable or disable the bookmark.

booking/[booking_id]/note
-------------------------
Notes can be added to bookings for reference.  These will be logged in the booking as being made by the account you are acting on behalf of, so can identify comments made by individual staff members. 

.. http:method:: POST /api/3.0/booking/{booking_id}/note

	:arg string booking_id: The unique booking code identifying a booking in the system.
	:param string body: The text to include in your booking note.  Up to 3000 chars.

