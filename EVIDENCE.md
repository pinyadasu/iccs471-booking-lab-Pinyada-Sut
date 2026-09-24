# Booking Lab Evidence Record

**Name :** Pinyada Suthisopha-aphorn
**Student ID :** 6580511
**Repository :** https://github.com/pinyadasu/iccs471-booking-lab-Pinyada-Sut

## Goal

The goal was to update create_booking so that overlapping bookings in the same room are rejected with ValueError and are not stored. Adjacent bookings and bookings with overlapping times in different rooms should still be accepted.

## Constraints / Out of Scope

The changes were limited to booking_app/booking.py and tests/test_booking.py. Existing validation and behavior were kept unchanged. demo.py and other files were not changed, and no extra features were added.

## Key Decision and Agent Claim

Copilot proposed adding an overlap check and tests for the new behavior. During the review, it was noticed that the assignment also required a case where a new booking is completely inside an existing booking. Copilot was asked to add a test for this case because it directly covered the assignment requirement.

Copilot also claimed that only the permitted files were changed. This was checked using git status and git diff, which showed that only booking_app/booking.py and tests/test_booking.py were modified.

## Verification : Claim → Evidence

- **Claim :** Same-room overlapping bookings should be rejected, while adjacent and different-room bookings should be accepted.
- **Command or test I ran :** uv run python -m unittest discover -s tests -v
- **Actual result :** 8 tests ran and all 8 passed with OK.
- **What this supports :** The tests covered same-room overlap, contained overlap, adjacent bookings, different-room bookings, and the original validation tests.

## Manual Validation

uv run python demo.py showed that the first booking in room A was accepted, the overlapping booking in room A was rejected, the adjacent booking in room A was accepted, and the overlapping time in room B was accepted. The final result was Stored bookings: 3, supporting that the rejected booking was not stored.

## Remaining Uncertainty

A more complex sequence involving several existing bookings was not specifically tested. The current tests cover the required cases but do not establish every possible multi-booking sequene.